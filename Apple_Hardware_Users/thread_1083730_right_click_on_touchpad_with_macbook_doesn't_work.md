---
title: "right click on touchpad with macbook doesn't work"
date: 2009-03-01
forum: Apple Hardware Users
---

### Post by Llewlyn on 2009-03-01
Hi to all community,
i've installed ubuntu on girlfriend's macbook and it works fine except the touchpad. The toy is a MacBook 2,1 with intrepid, kernel 2.6.27. Since she has 8.10 i've created a new .fdi file (reading permission by everyone) and i've pasted the content found in ubuntu macbook guide, that is basically this:

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
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">false</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">false</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">false</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">false</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>
        <merge key="input.x11_options.PalmDetect" type="string">1</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

i've expecting to see the right click working but nothing. I also tried to reconfigure xorg adding a new device in xorg.conf but it hadn't work. I think that maybe the .fdi was miswritten so i have used the .fdi and .deb found on [this page]("http://ubuntuforums.org/showthread.php?t=981474") but i haven't result.

That's the content of my log file:

```
(II) config/hal: Adding input device appletouch
(II) LoadModule: "synaptics"

(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 0.15.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(II) Synaptics touchpad driver version 0.15.2
(II) appletouch: x-axis range 0 - 1599
(II) appletouch: y-axis range 0 - 386
(**) Option "Device" "/dev/input/event9"
(--) appletouch touchpad found
(**) appletouch: always reports core events
(II) XINPUT: Adding extended input device "appletouch" (type: TOUCHPAD)
(II) appletouch: x-axis range 0 - 1599
(II) appletouch: y-axis range 0 - 386
(--) appletouch touchpad found

```

it seemms that it recognizes correctly the device, in fact it has all the function but the right-middle click (i've tried of course with 2 fingering, macosx way).

My question is: how the hal system works? i'm interesting in knowing which is the processed .fdi file (/var/log/Xorg.0.log didn't say!) and eventually see some error in my configuration.

Anyone can help?

Ll.

---

### Post by cyberdork33 on 2009-03-01
you need to completely remove the touchpad section from your xorg.conf. the two configs don't cooperate...

---

### Post by Llewlyn on 2009-03-01
i've done but it hasn't help :-(

Ll.

---

### Post by tiagobt on 2009-03-01
The .fdi file posted on the thread "Apple Touchpad: Improved Experience" will not give you a right click if you tap with two fingers (like Mac OS X). You have to lay two fingers on the touchpad and then press the button (ClickFinger behaviour).

If you want to right click by tapping with two fingers simultaneously (TapButton behavior), your .fdi file should be similar to the one you found in the Ubuntu MacBook Guide.

If you want to have both options, you can use the following file (ClickFinger + TapButton):

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

        <merge key="input.x11_options.RTCornerButton" type="string">false</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">false</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">false</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">false</merge>

        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1100</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>

        <merge key="input.x11_options.FingerLow" type="string">15</merge>
        <merge key="input.x11_options.FingerHigh" type="string">25</merge>

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

Be sure to place the file in the folder **/etc/hal/fdi/policy** and to use the extension **.fdi**. After that, remember to restart the X server (Ctrl + Alt + Backspace) or reload the driver with the following command:

```
sudo modprobe -r appletouch && sudo modprobe appletouch
```

Tiago

---

