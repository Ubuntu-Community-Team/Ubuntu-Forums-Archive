---
title: "Will multitouch work if I install ubuntu as native OS?"
date: 2010-02-16
forum: Apple Hardware Users
---

### Post by miatawnt2b on 2010-02-16
I hate OSX. I have however gotten very used to the multitouch trackpad on my aluminum MacbookPro. So, I would like to blow away OSX and install Ubuntu native. I was wondering if I will loose multitouch capability if I do this though.  Mainly 2 finger tap for right click, and two finger scroll.  My MacbookPro is rev 5,2.

Are there any other issues I should think about before taking the plunge?

Thanks,
-J

---

### Post by cgroza on 2010-02-16
try running ubuntu from a live cd, if multitouch works in livecd it should work with ubuntu.

---

### Post by linuxopjemac on 2010-02-17
there is a solution to this

   > 1.

      Create the file appletouch.fdi in the folder /etc/hal/fdi/policy:

     ```
 sudo gedit /etc/hal/fdi/policy/appletouch.fdi
```

   2. Paste the following contents into the file:

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

          <merge key="input.x11_options.PalmDetect" type="string">true</merge>
         </match>
        </match>
       </device>
      </deviceinfo>
```

   3. Restart the touchpad's kernel driver with the command:

    ```
  sudo modprobe -r appletouch && sudo modprobe appletouch
```

The following behavior should result:

    *

      Left click: one-finger tap or button press
    *

      Right click: two-finger tap or button press with two fingers on the pad
    *

      Middle click: three-finger tap or button press with three fingers on the pad
    *

      Vertical scrolling: move two fingers vertically 

taken from the [wiki]("https://help.ubuntu.com/community/MacBook2-1/Karmic#Touchpad%20(appletouch)")

---

### Post by zeroti on 2010-04-23
Is there a way to get this to work on a Powerbook? The above instructions didn't work for me.

Multitouch wasn't originally enabled by apple, but I was able to use it with iScroll2 on os x.

---

### Post by linuxopjemac on 2010-04-26
There is a multitouch driver available nowadys, still beta though, you will have to set it up yourself:


[http://ubuntuforums.org/showthread.php?t=1334696](http://ubuntuforums.org/showthread.php?t=1334696)

---

### Post by cph05a on 2010-04-26
> try running ubuntu from a live cd, if multitouch works in livecd it should work with ubuntu.

The driver on the live cd "works" but it is no good. Things like click and drag, thumb detection, etc won't work, but you can click on things. I'd get a new driver, such as the one posted above.

---

