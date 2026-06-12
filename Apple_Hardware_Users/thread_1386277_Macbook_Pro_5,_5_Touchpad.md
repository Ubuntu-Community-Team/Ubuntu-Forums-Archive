---
title: "Macbook Pro 5, 5 Touchpad"
date: 2010-01-20
forum: Apple Hardware Users
---

### Post by cph05a on 2010-01-20
I recently bought a macbook pro 5,5 (unibody) and I'm running both OSX and Ubuntu 9.10. I love the laptop, but I've been having some issues with the touchpad in karmic. 

In OSX, I can keep my thumb on the bottom of the touchpad as if it were a button and operate the rest of the touchpad as normal. With my thumb on the bottom of the pad, I can still click and drag and use two finger scrolling.

In ubuntu, I've used the instructions from 
[https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Touchpad](https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Touchpad)
If I have a thumb on the touchpad, it always assumes I'm two-finger scrolling. I've tried synclient BottomEdge=600, but it doesn't make any difference.

Has anyone gotten the touchpad to work well?

---

### Post by linuxopjemac on 2010-01-21
did you try gsynaptics to edit the touchpad behavior to your needs?

```
sudo apt-get install gsynaptics
```

---

### Post by cph05a on 2010-01-23
that's a nice app for sure, but it doesn't allow me to disable the bottom part of the touchpad

---

### Post by inphektion on 2010-01-24
try using the .fdi file described here:
[https://help.ubuntu.com/community/MacBookPro5-5/Jaunty#Touchpad](https://help.ubuntu.com/community/MacBookPro5-5/Jaunty#Touchpad)

---

### Post by cph05a on 2010-02-03
Okay here is my policy.fdi file:

```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
 <device>
  <match key="info.capabilities" contains="input.touchpad">
   <match key="info.product" contains="bcm5974">
   <merge key="appledevice" type="bool">true</merge>
   </match>

   <match key="appledevice" bool="true">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>
	<merge key="input.x11_options.BottomEdge" type="string">600</merge>

        <merge key="input.x11_options.FingerLow" type="string">40</merge>
        <merge key="input.x11_options.FingerHigh" type="string">70</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>

        <merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.15</merge>

        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">25</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">250</merge>
   </match>
  </match>
 </device>
</deviceinfo>
```

I took a guess and added the line
```

<merge key="input.x11_options.BottomEdge" type="string">600</merge>

```
but it didn't have any effect

---

