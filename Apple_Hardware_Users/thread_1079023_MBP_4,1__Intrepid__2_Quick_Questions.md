---
title: "MBP 4,1 | Intrepid | 2 Quick Questions"
date: 2009-02-23
forum: Apple Hardware Users
---

### Post by brentgrunenberg on 2009-02-23
Hi people, I have two quick questions:

1. I cant make the tap-to-click and double-tap-to-drag functions of the trackpad work, and I've grown used to this is OSX! I've seen a few things on here, modifying the xorg file for example but I cant seem to get it running. How is this done?

2. Im running the 32bit of Intrepid, should I be running the 64?

---

### Post by cyberdork33 on 2009-02-24
> **brentgrunenberg said:**
> 1. I cant make the tap-to-click and double-tap-to-drag functions of the trackpad work, and I've grown used to this is OSX! I've seen a few things on here, modifying the xorg file for example but I cant seem to get it running. How is this done?
Documentation for your hardware is here:
[https://help.ubuntu.com/community/MacBookPro4-1/Intrepid](https://help.ubuntu.com/community/MacBookPro4-1/Intrepid)

You should not have a touchpad section in your xorg.conf at all.

> **brentgrunenberg said:**
> 2. Im running the 32bit of Intrepid, should I be running the 64?
It is a matter of preference. See the FAQ at the top of the forum.

---

### Post by deltaiscain on 2009-02-25
> **brentgrunenberg said:**
> Hi people, I have two quick questions:

1. I cant make the tap-to-click and double-tap-to-drag functions of the trackpad work, and I've grown used to this is OSX! I've seen a few things on here, modifying the xorg file for example but I cant seem to get it running. How is this done?

2. Im running the 32bit of Intrepid, should I be running the 64?

2. i am, not sure if you have to. I have 4gb's of ram, only reason, plus the kernel addon messed up my wireless card, so i didn't do that again. 

1. I managed to get it to work. You have to download a couple packages: [link]("https://launchpad.net/~mactel-support/+archive/ppa") get the bcm9574 package, install it, and then download the xfree86-drivers-synaptics and install that. You might need to reboot before the next step. 
Open the terminal, and type ```
sudo nautilus
``` and go to your file system, then the folder **etc**, then the folder **hal**, then **fdi**, then **policy**, and copy and paste the preferences.fdi file in that folder. Rename the copied one to: bcm5974.fdi. Then open it with text editor, and replace everything with this:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>

    <match key="info.capabilities" contains="input.touchpad">
<!--
      <match key="info.product" contains="appletouch">
        <merge key="appledevice" type="bool">1</merge>
      </match>

      <match key="info.product" contains="bcm5974">
        <merge key="appledevice" type="bool">1</merge>
      </match>

      <match key="appledevice" bool="1">
-->
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

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
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.25</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">15</merge>
	<merge key="input.x11_options.LockedDrags" type="string">off</merge>
	<merge key="input.x11_options.LockedDragTimeout" type="string">1</merge>
<!--
      </match>
-->
    </match>
  </device>
</deviceinfo>
```
save, and then close the window, close the file browser window, and go to terminal and type: ```
sudo modprobe -r bcm5974 && sudo modprobe bcm5974
```
Then it should work. This already has the touch to click open. The only changes in it are the LockedDrags and the LockedDragTimeout. To find out what they are, and how to change them, open terminal and type ```
man synaptics
```

---

