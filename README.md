# Ex.No:2b To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

1.Start the Android application and display the first screen.
2.Get a number as input from the user using an EditText field.
3.When the user clicks the Factorial button, calculate or pass the entered number using an Explicit Intent.
4.Open the second screen (Activity) and receive the number from the first screen.
5.Calculate the factorial of the number and display the result on the second screen.

## PROGRAM:
```

Program to print the text “ExplicitIntent”.
Developed by: SACHIN J M
Registeration Number : 212225100041

```

### MainActivity.java

```java

package com.example.explicitintent;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

import java.math.BigInteger;

public class MainActivity extends AppCompatActivity {
    EditText numberInput;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
         numberInput = findViewById(R.id.editTextText);
    }

    public void newScreen(View view){
        String input = numberInput.getText().toString();
        if(input.isEmpty()){
            Toast t = Toast.makeText(this,"Please enter a number",Toast.LENGTH_LONG);
            t.show();
            return;
        }
        try{
            int n = Integer.parseInt(input);
            if(n<0){
                Toast t = Toast.makeText(this,"Please enter a non-negative number",Toast.LENGTH_LONG);
                t.show();
                return;
            }

            Integer fact = 1;
            for(int i=n;i>=1;i--) fact *=i;

            Intent i = new Intent(this,MainActivity2.class);
            i.putExtra("result",fact.toString());
            startActivity(i);

        }catch(NumberFormatException e){
            Toast.makeText(this, "Invalid number", Toast.LENGTH_LONG).show();
        }
    }
}
```

### activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="164dp"
        android:fontFamily="cursive"
        android:scaleX="2"
        android:scaleY="2"
        android:text="Experiment 2B - ExplicitIntent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/textView3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="60dp"
        android:fontFamily="sans-serif-black"
        android:scaleX="1.4"
        android:scaleY="1.3"
        android:text="SACHIN J M  -  212225100041"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView" />

    <TextView
        android:id="@+id/textView4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="48dp"
        android:scaleX="2"
        android:scaleY="2"
        android:text="Factorial Calculator"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView3" />

    <EditText
        android:id="@+id/editTextText"
        android:layout_width="200dp"
        android:layout_height="wrap_content"
        android:layout_marginTop="32dp"
        android:ems="10"
        android:inputType="number"
        android:hint="Enter a number"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView4" />

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="32dp"
        android:onClick="newScreen"
        android:text="Click to go... "
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editTextText" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
### MainActivity3.java
```java

package com.example.explicitintent;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity2 extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);
        TextView textView = findViewById(R.id.resultTextView);
        String result = getIntent().getStringExtra("result");
        if(result != null) textView.setText(result);
    }

    public void homeScreen(View view){
        Intent i = new Intent(this,MainActivity.class);
        startActivity(i);
    }
}


```
### activity_main3.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/linearLaylout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity3">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="180dp"
        android:fontFamily="cursive"
        android:scaleX="2"
        android:scaleY="2"
        android:text="Experiment 2B - ExplicitIntent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.507"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/textView3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="60dp"
        android:fontFamily="sans-serif-black"
        android:scaleX="1.4"
        android:scaleY="1.3"
        android:text="SACHIN J M  - 212225100041"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView" />

    <TextView
        android:id="@+id/textView4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="48dp"
        android:scaleX="2"
        android:scaleY="2"
        android:text="Factorial Result"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView3" />

    <TextView
        android:id="@+id/resultTextView"
        android:layout_width="347dp"
        android:layout_height="wrap_content"
        android:layout_marginTop="32dp"
        android:text="0"
        android:textAlignment="center"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView4" />

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="48dp"
        android:onClick="homeScreen"
        android:text="Click to Return... "
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/resultTextView" />

</androidx.constraintlayout.widget.ConstraintLayout>


```

## OUTPUT

<img width="1737" height="905" alt="2b" src="https://github.com/user-attachments/assets/4febe016-2706-42c8-9901-784ef8347e95" />
<img width="1729" height="910" alt="2b2" src="https://github.com/user-attachments/assets/f8f6399d-1518-43fa-9085-9f04796530ed" />
<img width="1730" height="909" alt="2b3" src="https://github.com/user-attachments/assets/8ec0fabb-79a8-43cb-8a01-561ceec9a4ad" />


## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


