---
title: "event numbers"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-09-30
I have a touch screen installed on my comp (fiesty 64) 

in my xorg.conf file:

Section "InputDevice"
    Identifier "touchscreen"
    Driver "egalax"
    Option "Device" "/dev/input/event4"
    Option "DeviceName" "touchscreen"
    Option "MinX" "0"
    Option "MinY" "0"
    Option "MaxX" "800"
    Option "MaxY" "600"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
    Option "SwapY" "1"
    Option "SwapX" "0"	
EndSection

when i do a cat /proc/bus/input/devices

I: Bus=0003 Vendor=0eef Product=0001 Version=0100
N: Name="eGalax Inc. USB TouchController"
P: Phys=/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse1 ts1 event2 
B: EV=b
B: KEY=400 0 0 0 0 0
B: ABS=3

The touch screen show up as event2.  But then sometimes it shows up as event 4.  I want to know if i can pin down the even on the touch screen or if there is a problem else where that could be causing this problem.
Thanks

---

