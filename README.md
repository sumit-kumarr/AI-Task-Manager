# AI-Task-Manager
AI_TASK_MANAGER

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
 xmlns:app="http://schemas.android.com/apk/res-auto"
 xmlns:tools="http://schemas.android.com/tools"
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 tools:context=".MainActivity"
 android:orientation="vertical"
 android:id="@+id/info" >
 <Button
 android:id="@+id/button1"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:onClick="fetchData"
 android:text="Start MULTITHREAD" />
 <TextView
 android:id="@+id/textView1"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content'
android:text="Main thread" />
/LinearLayout>




package com.example.pgm6;
import android.annotation.SuppressLint;
import android.app.Activity;
import android.os.Bundle;
import android.os.Handler;
import android.view.View;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
public class MainActivity extends AppCompatActivity {
 private TextView tvOutput;
 private static
 final int t1 = 1;
 private static final int t2 = 2;
 private static final int t3 = 3;
 @Override
 protected void onCreate(Bundle savedInstanceState) {
 super.onCreate(savedInstanceState);
 setContentView(R.layout.activity_main);
 tvOutput = (TextView) findViewById(R.id.textView1);
 }
 public void fetchData(View v) {
 tvOutput.setText("Main thread");
 thread1.start()
thread2.start();
 thread3.start();
 }
 Thread thread1 = new Thread(new Runnable() {
 @Override
 public void run() {
 for (int i = 0; i < 5; i++) {
 try {
 Thread.sleep(1000);
 } catch (InterruptedException e) {
 e.printStackTrace();
 }
 handler.sendEmptyMessage(t1);
 }
 }
 });
 //Thread2
 Thread thread2 = new Thread(new Runnable() {
 @Override
 public void
 run() {
 for (int i = 0; i < 5; i++) {
 try {
 Thread.sleep(1000);
 } catch (InterruptedException e) {
e.printStackTrace();
 }
 handler.sendEmptyMessage(t2);
 }
 }
 });
 //Thread3
 Thread thread3 = new Thread(new Runnable() {
 @Override
 public void
 run() {
 for (int i = 0; i < 5; i++) {
 try {
 Thread.sleep(1000);
 } catch (InterruptedException e) {
 e.printStackTrace();
 }
 handler.sendEmptyMessage(t3);
 }
 }
 });
 //Handler
 @SuppressLint("HandlerLeak")
 Handler handler = new Handler() {
 public void handleMessage(android.os.Message msg) {
if (msg.what == t1) {
 tvOutput.append("\nRunning thread 1");
 }
 if (msg.what == t2) {
 tvOutput.append("\nRunning thread 2");
 }
 if (msg.what == t3) {
 tvOutput.append("\nRunning thread 3");
 }
 }
 };
}
