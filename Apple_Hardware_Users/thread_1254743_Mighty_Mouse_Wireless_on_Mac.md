---
title: "Mighty Mouse Wireless on Mac"
date: 2009-08-31
forum: Apple Hardware Users
---

### Post by luigi.viggiano on 2009-08-31
I am using Apple's Mighty Mouse Wireless (bluetooth) on ubuntu 9.04.

I have the following problems:

1. After the startup, or the resume, the mouse doesn't get seen until I press the buttons. After a while this seems to wakeup the mouse and it starts working.

2. while I am writing on the keyboard sometime the mouse clicks by itself moving the focus outside or moving the cursor somewhere. This is incredibly annoying. I don't know if this is related to the mighty mouse or to me touching inadvertitely the touchpad... but it seems not related to the touchpad since if I don't do a touch by purpose it is able to detect "palm tapping" and ignore it. I think it's the mighty mouse sending events (maybe to keep alive the bluetooth connection).

Anybody noticing similar problems? Or having any hints?

This is how I configured the touchpad (if I get it correctly I wonder that "PalmDetect" is meant to prevent accidental taps)
```
$ cat /etc/hal/fdi/policy/11-x11-synaptics.fdi 
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using 
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        <merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
      </match>
      <match key="info.product" contains="bcm5974">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1280</merge>
        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>

        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>

        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>

        <merge key="input.x11_options.LockedDrags" type="string">1</merge>
        <merge key="input.x11_options.LockedDragTimeout" type="string">800</merge>

        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizScrollDelta" type="string">30</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">30</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.15</merge>

        <!--
        <merge key="input.x11_options.MaxTapTime" type="string">180</merge>
        <merge key="input.x11_options.MaxTapMove" type="string">2000</merge>
        <merge key="input.x11_options.MaxDoubleTapTime" type="string">180</merge>
        <merge key="input.x11_options.SingleTapTimeout" type="string">180</merge>
        -->

        <merge key="input.x11_options.PalmDetect" type="string">1</merge>

        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>

      </match>
    </match>
  </device>
</deviceinfo>

```

---

### Post by luigi.viggiano on 2009-09-03
The involuntary tap still happening with mighty mouse disabled. This restricts the problem to the touch pad.

I changed PalmDetection to those params:

$ synclient -l | grep -i Palm
    PalmDetect              = 1
    PalmMinWidth            = 8
    PalmMinZ                = 250


Nobody annoyed by those problems?

---

### Post by Locoxella on 2009-09-11
You could use syndaemon to temporarily disable your touchpad while typing.

[http://xpd259.blogspot.com/2009/05/disable-synaptics-touchpad-while-typing.html]("http://xpd259.blogspot.com/2009/05/disable-synaptics-touchpad-while-typing.html")

Im also used syndaemon and hal rules to disable/enable the touchpad when my mighty mouse got connected/disconnected. But you may need to enable something called SHMConfig to achieve this.

I envy you. My mighty mouse was working flawless on my Ubuntu Jaunty after some manual fixes. But last month I had to install Jaunty from scratch and now it seems that im totally forgot how to make the mouse work.

Cheers

---

### Post by luigi.viggiano on 2009-09-18
Hi. The only thing you need to do is to make your bluetooth "Always Visible" on the macbook and the mighty mouse will work.

---

