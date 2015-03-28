# Comparing [TabHost](http://developer.android.com/reference/android/widget/TabHost.html) with [ScrollableTabHost](http://code.google.com/p/mobyfactory-uiwidgets-android/source/browse/trunk/src/com/mobyfactory/uiwidgets/ScrollableTabActivity.java) #

[ScrollableTabHost](http://code.google.com/p/mobyfactory-uiwidgets-android/source/browse/trunk/src/com/mobyfactory/uiwidgets/ScrollableTabActivity.java) is designed such that you can easily convert existing application using [TabHost](http://developer.android.com/reference/android/widget/TabHost.html) to [ScrollableTabHost](http://code.google.com/p/mobyfactory-uiwidgets-android/source/browse/trunk/src/com/mobyfactory/uiwidgets/ScrollableTabActivity.java) easily.

To keep the example short, only 2 tabs are added to both [TabHost](http://developer.android.com/reference/android/widget/TabHost.html) and [ScrollableTabHost](http://code.google.com/p/mobyfactory-uiwidgets-android/source/browse/trunk/src/com/mobyfactory/uiwidgets/ScrollableTabActivity.java). [ScrollView](http://developer.android.com/reference/android/widget/ScrollView.html) in [ScrollableTabHost](http://code.google.com/p/mobyfactory-uiwidgets-android/source/browse/trunk/src/com/mobyfactory/uiwidgets/ScrollableTabActivity.java) will only appear if total width of all tabs combined exceeds the screen width of the device. Tabs are spaced out evenly just like [TabHost](http://developer.android.com/reference/android/widget/TabHost.html) if less tabs are available.

## [TabHost](http://developer.android.com/reference/android/widget/TabHost.html) ##
```
public class Demo_TabHost extends TabActivity {

    @Override 
    public void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);
        final TabHost tabHost = getTabHost();
       
        tabHost.add(tabHost.newTabSpec("0")
                      .setIndicator("title 0", getResources().getDrawable(R.drawable.star))
                      .setContent(new Intent(this, DemoActivity1.class)));

        tabHost.add(tabHost.newTabSpec("1")
                      .setIndicator("title 1", getResources().getDrawable(R.drawable.star))
                      .setContent(new Intent(this, DemoActivity2.class)));
    }

}
```

## [ScrollableTabHost](http://code.google.com/p/mobyfactory-uiwidgets-android/source/browse/trunk/src/com/mobyfactory/uiwidgets/ScrollableTabActivity.java) ##
```
public class Demo_TabHost extends ScrollableTabActivity {

    @Override 
    public void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);
        setDelegate(new SliderBarActivityDelegateImpl());
        setDefaultShade(RadioStateDrawable.SHADE_GRAY, RadioStateDrawable.SHADE_GREEN);
       
        this.addTab("title 0", R.drawable.star, new Intent(this, DemoActivity1.class));
        this.addTab("title 1", R.drawable.star, new Intent(this, DemoActivity2.class));
        commit();
    }

}
```