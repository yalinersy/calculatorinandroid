## EX:NO:5 Develop a program to create a simple calculator using android studio.
## Aim:
To create and design an android application for a simple calculator using android studio.
## EQUIPMENTS REQUIRED:
Android Studio(Latest Version)
## ALGORITHM:
Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as smsintent and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6:Display details give in MainActivity file.

Step 7: Save and run the application.
## PROGRAM:
```
/*
Program to create and design an android application simple calculator using Intent.
Developed by: Sri Yaline R
Registeration Number :212224040325
*/
```

MainActivity.java
```
package com.example.myapplication;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    private EditText editText;
    private TextView resultText;
    private Button addButton, subtractButton, multiplyButton, divideButton, equalButton, clearButton;
    private Button num1Button, num2Button, num3Button, num4Button;
    private Button num5Button, num6Button, num7Button, num8Button, num9Button, zeroButton, dotButton;
    private double num1, num2;
    private boolean isAddition, isSubtraction, isMultiplication, isDivision;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editText = findViewById(R.id.editText2);
        resultText = findViewById(R.id.resultText);
        clearButton = findViewById(R.id.clear_text);


        addButton = findViewById(R.id.add);
        subtractButton = findViewById(R.id.sub);
        multiplyButton = findViewById(R.id.mul);
        divideButton = findViewById(R.id.div);
        equalButton = findViewById(R.id.submit);

        num1Button = findViewById(R.id.num1);
        num2Button = findViewById(R.id.num2);
        num3Button = findViewById(R.id.num3);
        num4Button = findViewById(R.id.num4);
        num5Button = findViewById(R.id.num5);
        num6Button = findViewById(R.id.num6);
        num7Button = findViewById(R.id.num7);
        num8Button = findViewById(R.id.num8);
        num9Button = findViewById(R.id.num9);
        zeroButton = findViewById(R.id.zero);
        dotButton = findViewById(R.id.dot);

        addButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (editText.getText().length() > 0 && !hasOperator()) {
                    num1 = Double.parseDouble(editText.getText().toString());
                    isAddition = true;
                    editText.append(" + ");
                }
            }
        });

        subtractButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (editText.getText().length() > 0 && !hasOperator()) {
                    num1 = Double.parseDouble(editText.getText().toString());
                    isSubtraction = true;
                    editText.append(" - ");
                }
            }
        });

        multiplyButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (editText.getText().length() > 0 && !hasOperator()) {
                    num1 = Double.parseDouble(editText.getText().toString());
                    isMultiplication = true;
                    editText.append(" X ");
                }
            }
        });

        divideButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (editText.getText().length() > 0 && !hasOperator()) {
                    num1 = Double.parseDouble(editText.getText().toString());
                    isDivision = true;
                    editText.append(" / ");
                }
            }
        });

        clearButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                editText.setText("");
                resultText.setText("0");
                // Reset all flags
                isAddition = false;
                isSubtraction = false;
                isMultiplication = false;
                isDivision = false;
            }
        });

        equalButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String currentText = editText.getText().toString();
                String operator = getOperatorSymbol();
                
                if (!operator.isEmpty() && currentText.contains(operator)) {
                    String secondNumStr = currentText.substring(currentText.indexOf(operator) + operator.length());
                    if (!secondNumStr.isEmpty()) {
                        num2 = Double.parseDouble(secondNumStr);
                        if (isAddition) {
                            resultText.setText(String.valueOf(num1 + num2));
                        } else if (isSubtraction) {
                            resultText.setText(String.valueOf(num1 - num2));
                        } else if (isMultiplication) {
                            resultText.setText(String.valueOf(num1 * num2));
                        } else if (isDivision) {
                            if (num2 != 0) {
                                resultText.setText(String.valueOf(num1 / num2));
                            } else {
                                resultText.setText("Error");
                            }
                        }
                        // Reset all flags after calculation
                        isAddition = false;
                        isSubtraction = false;
                        isMultiplication = false;
                        isDivision = false;
                    }
                }
            }
        });

        num1Button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                editText.append("1");
            }
        });

        num2Button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                editText.append("2");
            }
        });

        num3Button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                editText.append("3");
            }
        });

        num4Button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                editText.append("4");
            }
        });

        num5Button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                editText.append("5");
            }
        });

        num6Button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                editText.append("6");
            }
        });

        num7Button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                editText.append("7");
            }
        });

        num8Button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                editText.append("8");
            }
        });

        num9Button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                editText.append("9");
            }
        });

        zeroButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                editText.append("0");
            }
        });

        dotButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String currentText = editText.getText().toString();
                String operator = getOperatorSymbol();
                String lastPart = currentText;
                if (!operator.isEmpty() && currentText.contains(operator)) {
                    lastPart = currentText.substring(currentText.indexOf(operator) + operator.length());
                }
                if (!lastPart.contains(".")) {
                    editText.append(".");
                }
            }
        });
    }

    private boolean hasOperator() {
        String text = editText.getText().toString();
        return text.contains(" + ") || text.contains(" - ") || text.contains(" X ") || text.contains(" / ");
    }

    private String getOperatorSymbol() {
        if (isAddition) return " + ";
        if (isSubtraction) return " - ";
        if (isMultiplication) return " X ";
        if (isDivision) return " / ";
        return "";
    }
}

```
activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:background="@color/white"
    android:gravity="center"
    android:padding="16dp">

    <EditText
        android:id="@+id/editText2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center_horizontal"
        android:textAlignment="center"
        android:focusable="false"
        android:focusableInTouchMode="false"
        android:layout_marginTop="40sp"
        android:textSize="30dp"
        android:hint="Enter the Value" />

    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center_horizontal"
        android:layout_marginTop="16dp"
        android:orientation="horizontal">

        <TextView
            android:id="@+id/result"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:textSize="20sp"
            android:text="Result: " />

        <TextView
            android:id="@+id/resultText"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:textSize="20sp"
            android:text="0" />
    </LinearLayout>

    <TableLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp">

        <TableRow
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:gravity="center">

            <Button
                android:id="@+id/num1"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="1" />

            <Button
                android:id="@+id/num2"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="2" />

            <Button
                android:id="@+id/num3"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="3" />

            <Button
                android:id="@+id/add"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="+" />
        </TableRow>

        <TableRow
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:gravity="center">

            <Button
                android:id="@+id/num4"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="4" />

            <Button
                android:id="@+id/num5"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="5" />

            <Button
                android:id="@+id/num6"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="6" />

            <Button
                android:id="@+id/sub"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="-" />
        </TableRow>

        <TableRow
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:gravity="center">

            <Button
                android:id="@+id/num7"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="7" />

            <Button
                android:id="@+id/num8"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="8" />

            <Button
                android:id="@+id/num9"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="9" />

            <Button
                android:id="@+id/mul"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="X" />
        </TableRow>

        <TableRow
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:gravity="center">

            <Button
                android:id="@+id/dot"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="." />

            <Button
                android:id="@+id/zero"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="0" />

            <Button
                android:id="@+id/clear_text"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="CE" />

            <Button
                android:id="@+id/div"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:backgroundTint="@color/white"
                app:strokeWidth="1dp"
                app:strokeColor="@color/black"
                android:textSize="15sp"
                android:textColor="@color/black"
                android:text="/" />
        </TableRow>

    </TableLayout>


    <Button
        android:id="@+id/submit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:layout_marginTop="40dp"
        android:backgroundTint="@color/white"
        app:strokeWidth="1dp"
        app:strokeColor="@color/black"
        android:textSize="15sp"
        android:textColor="@color/black"
        android:text="Submit" />


</LinearLayout>
```
## OUTPUT

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/71a91516-409c-4e92-a261-04602f24ec02" />


## RESULT
Thus a Simple Android Application create a simple calculator using Android Studio is developed and executed successfully.
