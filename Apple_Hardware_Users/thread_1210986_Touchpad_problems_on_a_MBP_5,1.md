---
title: "Touchpad problems on a MBP 5,1"
date: 2009-07-12
forum: Apple Hardware Users
---

### Post by GeneralSunTzu on 2009-07-12
Hello,
am plagued by a jumpy touchpad on a MacBook Pro 5,1 with Jaunty.
Particularly mysterious is an irritating and unintelligible jumping between the Ubuntu equivalent of Spaces: I see a box with two arrows, one on the left and one on the right, and a small cursor movement will relentlessy move between these two.
Also, am unable to click and drag an object.
Only thanks to an external mouse I am able to use this MBP.
Have followed every recommendation on the appropriate wiki and here is the file am using:
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.touchpad">
   <match key="info.product" contains="bcm5974">
   <merge key="appledevice" type="bool">true</merge>
   </match>
  
   <match key="appledevice" bool="true">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

        <merge key="input.x11_options.FingerLow" type="string">120</merge>
        <merge key="input.x11_options.FingerHigh" type="string">200</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">0</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">0</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">0</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>

        <merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">0</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.2</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">2.0</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.10</merge>

        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">25</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">250</merge>
   </match>
  </match>
 </device>
</deviceinfo>

Some questions: is there here anything manifestly wrong?
What the hell is "palm detect"? (man synaptics does not explain it clearly)
What could I change to get rid of this problem?
Thank you very much.

---

### Post by nathanid95 on 2009-12-05
I've had the same problems when running Ubuntu from a LiveDVD on my MacBook Pro. Ubuntu, by default, has no installed drivers for using the advanced Multi-touch capabilities of an MBP. They run in a simple Raw Mode, which means they have minimal functionality as opposed to Mac OS functionality. You can adjust your touchpad sensitivity and acceleration settings from the Mouse settings panel.

---

