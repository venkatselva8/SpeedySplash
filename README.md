# SpeedySplash ![SpeedySplash AppLogo](https://github.com/venkatselva8/SpeedySplash/blob/master/app/src/main/res/mipmap-mdpi/ic_launcher.png) 
An Android Studio example project on how to implement a Speed- Splash Screen in Android


###SpeedySplash- Brand Theme

  SpeedySplash screen has single [Brand Image](https://github.com/venkatselva8/SpeedySplash/blob/master/app/src/main/res/drawable/splash_brand_img.png).  
  To achieve this, use the [SpeedyBrandTheme](https://github.com/venkatselva8/SpeedySplash/blob/master/app/src/main/res/values/styles.xml) in AndroidManifest.xml
 
  ![SpeedySplashBrand GIF](https://github.com/venkatselva8/SpeedySplash/blob/master/GitFiles/SpeedyBrand.gif)
-----
 
###SpeedySplash- AppLogo Theme

  SpeedySplash screen contains only AppLogo at the center of the screen.  
  To achieve this, use the [SpeedyTheme](https://github.com/venkatselva8/SpeedySplash/blob/master/app/src/main/res/values/styles.xml) in AndroidManifest.xml
 
  ![SpeedySplashBrand GIF](https://github.com/venkatselva8/SpeedySplash/blob/master/GitFiles/Speedy.gif)



## What is Splash Screen (or) Launch Screen ?

 The launch screen is a user’s first experience of your application. 
 More info [here](https://www.google.com/design/spec/patterns/launch-screens.html#)

## Purpose of Splash Screen

 The purpose of splash screen depends upon the app requirement.

 Main Purpose of SplashScreen which I know:

 1. To Show app logo. (SpeedySplash- AppLogo Theme)
 2. To Show case app logo & Company Brand Name. (SpeedySplash- Brand Theme)
 3. Show SplashScreen when making network calls (Http)
 4. Downloading Data and storing it in SQLite
 5. Fetching and Parsing Json/ XML
 6. Sending device information/ registering the device to our server.
 

## How to implement the Speedy Splash Screen
  Implementing a Speedy Splash Screen, is a little different than you might imagine. 
  The splash view that you see has to be ready immediately, even before you can inflate a layout file in your splash activity.
  **So you will not use a layout file. Instead, specify your splash screen’s background as the activity’s theme background. 
  To do this, first create an XML drawable in res/drawable.**
  
 1.res/drawable/splash_brand_layer.xml. 
 Here, I’ve set up a [Brand image](https://github.com/venkatselva8/SpeedySplash/blob/master/app/src/main/res/drawable/splash_brand_img.png). ( That image contains App Logo & Company Brand Name and size of 720px x 1280px )

```xml
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">

    <item>
        <bitmap
            android:gravity="fill"
            android:src="@drawable/splash_brand_img" />
    </item>

</layer-list>
```
 2.Next, you will set this as your splash activity’s background in the theme. 
 Navigate to your styles.xml file and add a new theme for your splash activity.

```xml   
   <resources>

    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.Light.DarkActionBar">
        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
        <item name="colorAccent">@color/colorAccent</item>
    </style>


    <!-- SpeedyTheme Style which simply shows the App Logo. -->
    <style name="SpeedyTheme" parent="Theme.AppCompat.NoActionBar">
        <item name="android:windowBackground">@drawable/splash_layer</item>
    </style>

    <!-- SpeedyBrandTheme Style which shows the single drawable Image.
         (I designed that image contains App Logo & Company Brand Name and size of 720px x 1280px ) -->
    <style name="SpeedyBrandTheme" parent="Theme.AppCompat.NoActionBar">
        <item name="android:windowBackground">@drawable/splash_brand_layer</item>
    </style>

</resources>
```
 3.Configure any one Style Theme as your splash activity’s theme in your AndroidManifest.xml
```xml
 <activity
            android:name="com.venkyapps.speedysplash.SplashActivity"
            android:theme="@style/SpeedyBrandTheme">

            <!-- If you want only App Logo in Splash Screen. Just change
                 android:theme="@style/SpeedyTheme"    -->
             <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>

  </activity>
```
 4.Atlast, Add the SplashActivity.java file in your project.
   (SplashActivity class which runs a timer to Intent to the MainActivity)

```java
    public class SplashActivity extends AppCompatActivity {
    // Splash screen timer
    private static int SPLASH_TIME_OUT = 2000;  //2 Seconds
     @Override
     protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        new Handler().postDelayed(new Runnable() {
            /*
             * Showing splash screen with a timer. This will be useful when you
             * want to show case your app logo / company
             */
            @Override
            public void run() {
                // This method will be executed once the timer is over
                // Start your app main activity
                Intent i = new Intent(SplashActivity.this, MainActivity.class);
                startActivity(i);
                // close this activity
                finish();
            }
        }, SPLASH_TIME_OUT);
    }
```    

##Credits

Thanks to the following for use of their works in my project.

1. App Icon              - [GitHub Octicons](https://octicons.github.com/)
2. App Icon creator tool - [Iconion](http://iconion.com/)
3. App Icon Resizer      - [MakeAppIcon](http://makeappicon.com/)

##End
Suggestions are welcome. Sent to venkatselva8@gmail.com

Happy Coding :)
