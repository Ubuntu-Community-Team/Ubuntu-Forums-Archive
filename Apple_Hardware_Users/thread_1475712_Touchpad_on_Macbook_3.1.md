---
title: "Touchpad on Macbook 3.1"
date: 2010-05-07
forum: Apple Hardware Users
---

### Post by abhiomkar on 2010-05-07
Hello there!

I've upgraded my Ubuntu from 9.10 to 10.04 recently on my Macbook 3.1. Everything works fine except the issue with touchpad which is really annoying. The touchpad movement is very bad. Also, I need press hard to move the cursor. 
The two finger scroll works fine.

The content of my /etc/hal/fdi/policy/appletouch.fdi file.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.touchpad">
   <match key="info.product" contains="appletouch">
    <merge key="input.x11_driver" type="string">synaptics</merge>
    <merge key="input.x11_options.SHMConfig" type="string">true</merge>

    <merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
    <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
    <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
    <merge key="input.x11_options.HorizTwoFingerScroll" type="string">false</merge>

    <merge key="input.x11_options.VertScrollDelta" type="string">20</merge>

    <merge key="input.x11_options.RTCornerButton" type="string">false</merge>
    <merge key="input.x11_options.RBCornerButton" type="string">false</merge>
    <merge key="input.x11_options.LBCornerButton" type="string">false</merge>
    <merge key="input.x11_options.LTCornerButton" type="string">false</merge>

    <merge key="input.x11_options.TopEdge" type="string">0</merge>
    <merge key="input.x11_options.LeftEdge" type="string">0</merge>
    <merge key="input.x11_options.RightEdge" type="string">1100</merge>
    <merge key="input.x11_options.BottomEdge" type="string">800</merge>

    <merge key="input.x11_options.FingerLow" type="string">5</merge>
    <merge key="input.x11_options.FingerHigh" type="string">15</merge>

    <merge key="input.x11_options.TapButton1" type="string">1</merge>
    <merge key="input.x11_options.TapButton2" type="string">3</merge>
    <merge key="input.x11_options.TapButton3" type="string">2</merge>

    <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
    <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
    <merge key="input.x11_options.ClickFinger3" type="string">2</merge>

    <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
    <merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
    <merge key="input.x11_options.AccelFactor" type="string">0.15</merge>

    <merge key="input.x11_options.PalmDetect" type="string">yes</merge>
   </match>
  </match>
 </device>
</deviceinfo>
```

Any suggestions to fix this issue to work touchpad same like in Mac OS X.

Thanks in advance!

---

### Post by kcirrab on 2011-06-23
i double this. i have to push annoyingly hard to get the trackpad to move which screws me up all the time i am always misclicking stuff i would really like a solution to this and please DO NOT just tell me to get a mouse... i know that that is a solution but not the one i am looking for. if i cannot get this resolved i might have to just go back to os x

---

### Post by AlexPogue on 2011-07-01
Yes, this is definitely an issue. Somebody please help!

---

