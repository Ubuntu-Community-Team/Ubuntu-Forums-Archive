---
title: "Want to get my Webcam Working"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-07-05
I want a HP Pavilion dv9000 and want to get my webcam working.
I've tried other posts with the same computer model, but I don't think it was the right camera.

Where do I start?  I guess i have to find out what camera is in the computer.
How would I do this?

---

### Post by Raineer on 2007-07-05
You might try giving [this]("http://mxhaard.free.fr/") site a try, there are a ton of drivers here.

---

### Post by chris062689 on 2007-07-05
Ok cool, but how do I find out which one I'm using?

---

### Post by Raineer on 2007-07-05
I don't know anything about your PC but you can try the following code:
```
cat /proc/bus/input/devices
``` 
in a terminal window and it will give a lot of information about your USB bus.  You may be able to scroll through and find information that matches your kind of camera.

---

### Post by chris062689 on 2007-07-05
chris@ubuntu:~$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 ts0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120013
B: KEY=1004 2200002 3802078 f950d401 feffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0007 Version=0000
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse1 ts1 event2 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=ACPI_FPB/button/input0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input4
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/class/input/input5
H: Handlers=kbd event5 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input6
H: Handlers=event6 
B: EV=21
B: SW=1

chris@ubuntu:~$

---

### Post by chris062689 on 2007-07-05
Contacted HP support; found my driver for the HP Pavilion dv9000 here.
[http://royale.zerezo.com/zr364xx/](http://royale.zerezo.com/zr364xx/)

Tested, works great!

---

### Post by ajesh on 2007-07-11
Did you have to download the latest kernel source and build it with support for this driver?

Could you let me know on how you did it.

Thanks,
-Ajesh

---

### Post by asatishc on 2007-08-02
I installed the drivers, tested the webcam with ekiga. works perfectly fine.
But the problem is I cant get the webcam work on other applications like camorama, xawtv etc.
Camora gives an error saying Cannot find device /dev/video0
Can anyone give any suggestions?

---

