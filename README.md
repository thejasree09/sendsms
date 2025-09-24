[
# Ex.No:6 Design an android application Send SMS using Intent.


## AIM:

To create and design an android application Send SMS using Intent using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as smsintent and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Send SMS and Display details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to create and design an android application Send SMS using Intent.
Developed by: THEJA SREE G
Registeration Number : 212224110056
*/
```

## PROGRAM

activity_main.xml

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp"
    android:orientation="vertical">

    <EditText
        android:id="@+id/etPhoneNumber"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Phone Number"
        android:inputType="phone" />

    <EditText
        android:id="@+id/etMessage"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Message"
        android:inputType="textMultiLine"
        android:lines="4" />

    <Button
        android:id="@+id/btnSendSMS"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Send SMS"
        android:layout_marginTop="16dp"/>
</LinearLayout>

```

MainActivity.java

```
package com.example.myapplication;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText etPhoneNumber, etMessage;
    Button btnSendSMS;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etPhoneNumber = findViewById(R.id.etPhoneNumber);
        etMessage = findViewById(R.id.etMessage);
        btnSendSMS = findViewById(R.id.btnSendSMS);

        btnSendSMS.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String phone = etPhoneNumber.getText().toString().trim();
                String message = etMessage.getText().toString().trim();

                if (phone.isEmpty() || message.isEmpty()) {
                    Toast.makeText(MainActivity.this, "Please enter number and message", Toast.LENGTH_SHORT).show();
                } else {
                    sendSMSUsingIntent(phone, message);
                }
            }
        });
    }

    private void sendSMSUsingIntent(String phone, String message) {
        Intent intent = new Intent(Intent.ACTION_SENDTO);
        intent.setData(Uri.parse("smsto:" + phone));  // Only SMS apps can handle this
        intent.putExtra("sms_body", message);

        try {
            startActivity(intent);
        } catch (Exception e) {
            Toast.makeText(this, "No SMS app found", Toast.LENGTH_SHORT).show();
        }
    }
}

```

AndroidManifest.xml

```
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.myapplication">

    <application
        android:allowBackup="true"
        android:label="Send SMS Intent"
        android:supportsRtl="true"
        android:theme="@style/Theme.AppCompat.Light.NoActionBar">

        
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

    </application>
</manifest>

```

## OUTPUT

<img width="1919" height="1079" alt="Screenshot 2025-09-22 133947" src="https://github.com/user-attachments/assets/14778d1f-ab18-4a29-9e53-feecc9ae4f8a" />

<img width="1919" height="1079" alt="Screenshot 2025-09-22 134431" src="https://github.com/user-attachments/assets/1816b21c-9e7b-4997-9c83-71ef3bcf5113" />

<img width="1919" height="1079" alt="Untitled design (12)" src="https://github.com/user-attachments/assets/6a30d05d-ac0c-4f21-af23-f64a92223a88" />

<img width="1919" height="1079" alt="Untitled design (13)" src="https://github.com/user-attachments/assets/ad8b1de4-6426-410d-8849-5423c458eb29" />

<img width="1919" height="1079" alt="Untitled design (16)" src="https://github.com/user-attachments/assets/9aab3626-c32c-4c22-911c-85c167a89ba9" />

<img width="1919" height="1079" alt="Untitled design (15)" src="https://github.com/user-attachments/assets/a6ffb443-53b5-4587-a45c-ec16a51edc74" />



## RESULT
Thus a Simple Android Application create and design an android application Send SMS using Intent using Android Studio is developed and executed successfully.
](https://github.com/aswethaashok/sendsms)
