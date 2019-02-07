# Android Image Slider [![Build Status](https://travis-ci.org/daimajia/AndroidImageSlider.svg)](https://travis-ci.org/daimajia/AndroidImageSlider)

[![Gitter](https://badges.gitter.im/Join Chat.svg)](https://gitter.im/daimajia/AndroidImageSlider?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
 
This is an amazing image slider for the Android platform. I decided to open source this because there is really not an attractive, convenient slider widget in Android.
 
You can easily load images from an internet URL, drawable, or file. And there are many kinds of amazing animations you can choose. :-D

## Step-1:Add gradle dependencies

   dependencies {

    implementation "com.android.support:support-v4:+"
    
    implementation 'com.squareup.picasso:picasso:2.3.2'
    
    implementation 'com.nineoldandroids:library:2.4.0'
    
    implementation 'com.daimajia.slider:library:1.1.5@aar'
    
   }

# Step-2 Add the Slider to your layout:

 

    <com.daimajia.slider.library.SliderLayout

        android:id="@+id/slider"
        
        android:layout_width="match_parent"
        
        android:layout_height="200dp"
        
     />

# Step-3 Write Correspondin Java code in Activity class

SliderLayout mDemoSlider;

in onCreate() method instantiate it

        mDemoSlider = findViewById(R.id.slider);


        
        HashMap<String,Integer> file_maps = new HashMap<String, Integer>();
        file_maps.put("Hannibal",R.drawable.photo);
        file_maps.put("Big Bang Theory",R.drawable.photo);
        file_maps.put("House of Cards",R.drawable.photo);
        file_maps.put("Game of Thrones",R.drawable.photo);

        for(String name : file_maps.keySet()){
            TextSliderView textSliderView = new TextSliderView(this);
            // initialize a SliderLayout
            textSliderView
                    .description(name)
                    .image(file_maps.get(name))
                    .setScaleType(BaseSliderView.ScaleType.Fit);

            //add your extra information
            textSliderView.bundle(new Bundle());
            textSliderView.getBundle()
                    .putString("extra",name);

            mDemoSlider.addSlider(textSliderView);
        }
        mDemoSlider.setPresetTransformer(SliderLayout.Transformer.Accordion);
        mDemoSlider.setPresetIndicator(SliderLayout.PresetIndicators.Center_Bottom);
        mDemoSlider.setCustomAnimation(new DescriptionAnimation());
        mDemoSlider.setDuration(4000);
        
