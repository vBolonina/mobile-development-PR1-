# Практическая работа №1 Знакомство с Android Studio
Выполнила: Болонина Валерия Романовна ИНС-б-о-24-2 Вариант:9
# Цель работы
Изучение интерфейса Android studio и создание первого простого приложения
# Ход работы
1. В начале работы был скачан и настроен Android Studio согласно методичке. Был создан и запущен новый проект "My Application"
<img width="2096" height="1389" alt="image" src="https://github.com/user-attachments/assets/7bae99e1-f03f-4038-b87c-360ecfd6829b" />
2. В названии приложения указано авторство путем изменения содержимого файла "strings.xml"
<img width="667" height="197" alt="image" src="https://github.com/user-attachments/assets/987dea9c-8513-4765-b45f-53edeed00834" />

На странице приложения указана дата рождения с помощью свойства страницы TextView.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b6fa1eb5-e9e9-45b2-9df2-1671d2fe81df" />
3. На третьем этапе было выполнено индивидуальное задание согласно варианту. В соответствии с условием, был отрисован оранжевый квадрат, площадь которого в 2 раза меньшн площади экрана.
# Листинг 1 - класс DrawView для задания 3
## Листинг 1 - класс DrawView для задания 3

```java
package com.example.myapplication;

import android.content.Context;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.os.Bundle;
import android.view.View;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        DrawView drawView = new DrawView(this);
        setContentView(drawView);
        setTitle("Оранжевый квадрат");
    }
}

class DrawView extends View {
    private Paint paint;
    
    public DrawView(Context context) {
        super(context);
        paint = new Paint();
    }

    @Override
    protected void onDraw(Canvas canvas) {
        super.onDraw(canvas);
        
        int screenWidth = getWidth();
        int screenHeight = getHeight();
        int sideLength = (int) Math.sqrt((screenWidth * screenHeight) / 2);
        
        canvas.drawRGB(255, 255, 255);
        paint.setColor(Color.parseColor("#FFA500"));
        paint.setStyle(Paint.Style.FILL);
        
        int left = (screenWidth - sideLength) / 2;
        int top = (screenHeight - sideLength) / 2;
        canvas.drawRect(left, top, left + sideLength, top + sideLength, paint);
    }
}
```

<img width="644" height="1025" alt="image" src="https://github.com/user-attachments/assets/222f2d1f-08c5-4d1c-b530-b2e9153db31f" />

4. Выполнено задание 4 согласно варианту: отрисовать ножницы
# Листинг 2 - класс DrawView для задания 4
```java
package com.example.myapplication;

import android.content.Context;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;
import android.graphics.Path;
import android.view.View;
import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(new DetailedScissorsView(this));
    }

    class DetailedScissorsView extends View {
        public DetailedScissorsView(Context context) {
            super(context);
        }

        @Override
        protected void onDraw(Canvas canvas) {
            super.onDraw(canvas);

            Paint paint = new Paint();
            paint.setAntiAlias(true);
            paint.setStrokeCap(Paint.Cap.ROUND); // Делает концы линий закругленными

            float cx = getWidth() / 2f;
            float cy = getHeight() / 2f;

            // 1. ЛЕЗВИЯ (Просто две толстые линии)
            paint.setColor(Color.GRAY);
            paint.setStrokeWidth(25f);
            paint.setStyle(Paint.Style.STROKE);

            // Первое лезвие (от ручки к кончику)
            canvas.drawLine(cx - 80, cy + 80, cx + 150, cy - 200, paint);
            // Второе лезвие
            canvas.drawLine(cx + 80, cy + 80, cx - 150, cy - 200, paint);

            // 2. РУЧКИ (Два простых круга)
            paint.setColor(Color.RED);
            paint.setStrokeWidth(15f);

            // Левое кольцо
            canvas.drawCircle(cx - 100, cy + 120, 45, paint);
            // Правое кольцо
            canvas.drawCircle(cx + 100, cy + 120, 45, paint);

            // 3. ЦЕНТР (Винтик)
            paint.setStyle(Paint.Style.FILL);
            paint.setColor(Color.BLACK);
            canvas.drawCircle(cx, cy, 8, paint);
        }
    }
}
```
<img width="679" height="1062" alt="Снимок экрана 2026-03-02 233930" src="https://github.com/user-attachments/assets/148db201-50b8-491c-bed4-e01759475cdc" />

## Вывод 
В ходе практической работы был изучен интерфейс Android Studio и создано первое приложение.
