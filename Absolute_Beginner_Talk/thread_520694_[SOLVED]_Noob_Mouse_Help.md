---
title: "[SOLVED] Noob Mouse Help"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by scb0825 on 2007-08-08
Hello all! I have been looking through the forums for a few days now trying to figure out how to get my MX5000 bluetooth mouse to work properly. The mouse works fine; my problem is with the buttons. I would like to forward/back buttons to work... especially in Firefox. I have tried several things, but no luck yet. I'm sure there is something simple I am missing... if anyone can help I would appreciate it. Thanks! :)

--Update--
Below is some info from my machine, I hope this helps. I just installed ubuntu a few days ago and would really like to get this sucker working... since I have been spoiled with the back button on the mouse :) 

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
B: KEY=1007 2002000 4380207a f840d001 feffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=045e Product=008c Version=0111
N: Name="Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/class/input/input5
H: Handlers=mouse1 ts1 event2 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input8
H: Handlers=kbd event5 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=ACPI_FPB/button/input0
S: Sysfs=/class/input/input9
H: Handlers=kbd event6 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input10
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0003 Vendor=046d Product=c70e Version=0111
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1d.2-1.2/input0
S: Sysfs=/class/input/input11
H: Handlers=kbd event3 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c70a Version=0111
N: Name="Logitech Logitech BT Mini-Receiver"
P: Phys=usb-0000:00:1d.2-1.3/input0
S: Sysfs=/class/input/input12
H: Handlers=kbd mouse2 ts2 event4 
B: EV=f
B: KEY=7fff 2c3027 bf004440 0 0 fff0001 f80 8807c000 667bfa d941dfed 9e0000 0 0 0
B: REL=143
B: ABS=1 0

-------------------------------------------------------------------------------------------

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

---

### Post by ron999 on 2007-08-08
Hi
Mine isn't a bluetooth mouse, but I got the buttons to work by following the instructions at this website here:-[http://www.cs.cornell.edu/~djm/ubuntu/#enable-5button-mouse]("http://www.cs.cornell.edu/~djm/ubuntu/#enable-5button-mouse")
:cool:

---

### Post by scb0825 on 2007-08-08
> **ron999 said:**
> Hi
Mine isn't a bluetooth mouse, but I got the buttons to work by following the instructions at this website here:-[http://www.cs.cornell.edu/~djm/ubuntu/#enable-5button-mouse]("http://www.cs.cornell.edu/~djm/ubuntu/#enable-5button-mouse")
:cool:

Thanks for the link; however, it did not change anything for me. :(

---

### Post by scb0825 on 2007-08-08
I kept searching and found the fix for my mouse... it's at the end of this post. 

[http://ubuntuforums.org/showthread.php?t=399374&highlight=mouse+forward+back+buttons](http://ubuntuforums.org/showthread.php?t=399374&highlight=mouse+forward+back+buttons)

---

### Post by amazingtaters on 2007-08-08
I just did this with my MX400. I would use this howto: [http://ubuntuforums.org/showthread.php?t=97936](http://ubuntuforums.org/showthread.php?t=97936) 
I believe the MX5000 set comes with the MX1000 mouse and a keyboard, yes?

---

