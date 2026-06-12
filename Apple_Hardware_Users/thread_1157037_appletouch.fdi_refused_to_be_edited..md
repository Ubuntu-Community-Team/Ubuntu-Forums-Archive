---
title: "appletouch.fdi refused to be edited."
date: 2009-05-12
forum: Apple Hardware Users
---

### Post by SaiHayashi on 2009-05-12
Hi all,

I have been following the guide to install jaunty on macbook4,1 on the ubuntu wiki site. [https://help.ubuntu.com/community/MacBook4-1/Jaunty]("https://help.ubuntu.com/community/MacBook4-1/Jaunty")

everything worked except the trackpad doesnt work the way as i would expect it to.
using the appletouch.fdi code provided, i was able to enable multi-touch trackpad.  The only problem is that instead of two finger tap/click as right click and three finger tap/click as middle click, it is reversed when i applied it.  At first i thought i mixed the order around so i went into appletouch.fdi and swapped the the string over.  but HAL doesnt seem to update it.

Can anyone suggest what is wrong with my configuration?

my fdi is identical to the one in wiki, which is:
> <?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
   <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
   <merge key="input.x11_options.TapButton1" type="string">1</merge>
   <merge key="input.x11_options.TapButton2" type="string">3</merge>
   <merge key="input.x11_options.TapButton3" type="string">2</merge>
   <merge key="input.x11_options.FingerLow" type="string">10</merge>
   <merge key="input.x11_options.FingerHigh" type="string">20</merge>
   <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
   <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
   <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
   <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
  </match>
 </device>
</deviceinfo>

---

### Post by cyberdork33 on 2009-05-12
check out this bug:
[https://bugs.edge.launchpad.net/mactel-support/+bug/337935](https://bugs.edge.launchpad.net/mactel-support/+bug/337935)

---

### Post by SaiHayashi on 2009-05-13
ok thx.  As I couldnt wait i decided to wipe the system (:( i know is noobish) and installed fresh again.  Then i managed to google up a solution using xorg.conf
ill attach here in case anyone is interested.

> Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "CorePointer"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "LeftEdge" "100"
	Option "RightEdge" "1120"
	Option "TopEdge" "50"
	Option "BottomEdge" "310"
	Option "FingerLow" "20"
	Option "FingerHigh" "30"
	Option "MaxTapTime" "150"
	Option "MaxTapMove" "220"
	Option "MaxDoubleTapTime" "180"
	Option "VertScrollDelta" "25"
	# Option "HorizScrollDelta" "30"
	Option "VertTwoFingerScroll" "true"
	Option "HorizTwoFingerScroll" "true"
	# Option "FastTaps" "true"
	Option "TapButton2" "3"
	Option "TapButton3" "2"
	Option "ClickFinger2" "3"
	Option "ClickFinger3" "2"
	Option "MinSpeed" "0.69"
	Option "MaxSpeed" "0.78"
	Option "AccelFactor" "0.015"
	Option "SHMConfig" "on"
EndSection

---

### Post by cyberdork33 on 2009-05-13
note that having the xorg config and the fdi file will cause conflicts. Be sure to only have one or the other.

---

