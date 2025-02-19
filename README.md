# Fifteen Million Merits / FMMAdvertisementView

This package FMMAdvertisementView is an accelerometer-based implementation of the dystopian advertising scheme featured in S01E02 of Black Mirror. The goal of the package is to detect user participation in watching pushed advertisements and pause the advertisement while the user is not participating.

That said, this is designed as a dystopian tech-demo not for commercial use. 

![alt text](./repo-resources/screens/obstructed-view-1.png "Title")

Rather than tap into the front facing camera and use eye-tracking algorithms, this package takes a simpler, less computational, and less invasive approach by tapping into the device's accelerometers to capture the change in orientation of the device and detect likely changes in viewing. 


### Getting Started

A quick demo project is attached: a simple mockup of a 2048 game with a button in the bottom right corner to launch a Black Mirror themed Wraith Girls advertisement. 

[A video of the demo is available on Vimeo.](https://vimeo.com/440092448/d45417e215)

For your own application, create a FMMAdvertisementView object and set the image (video advertisement support coming soon) through the adImageView property. You are then able to set a custom mandatory watch length by modifying the ad_duration [seconds] parameter and you can set the strictness parameter [0,100] to determine how little of a change in the orientation data will trigger the obstructed view alert. If desired you also have the ability to set an audio backing to your ad that will pause during view obstructions. 

Once your properties are set add the advertisement to your view and call the startTimer() method for the FMMAdvertisingView object. 

```objective-c
FMMAdvertisementView *your_ad  = [[FMMAdvertisementView alloc] initWithFrame:example_superview.frame];
[your_ad setAdImage:[UIImage imageNamed:@"example.png"]];              // load the image for your ad
[your_ad setAdAudioWithName:@"example_audio" andExtension:@"mp3"];     // audio backing for your ad
your_ad.strictness             = 50;                                   // the default setting [0,100]
your_ad.duration               = 15;                                   // seconds
[example_superview addSubview:your_ad];
[your_ad startTimer];                                                  // begin watch countdown
```

![Ad Demo](./repo-resources/app-screens/ad_demo.PNG "Ad Demo")  ![Obstructed Demo](./repo-resources/app-screens/obstructed_demo.PNG "Obstructed Demo")


### Requirements:

CoreMotion: deviceMotionAvailable: iOS 4.0+


### Additional Notes

I haven't checked explicitly, but I imagine that advertising in this fashion would result in App Rejection by Apple. This package is designed as a dystopian tech demo, not for commercial use. 

### Authors

* **Teddy Rowan**
