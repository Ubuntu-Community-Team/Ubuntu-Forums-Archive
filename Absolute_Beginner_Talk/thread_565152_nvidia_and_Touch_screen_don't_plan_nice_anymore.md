---
title: "nvidia and Touch screen don't plan nice anymore"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-10-01
So yesterday I set up my touch screen first and then managed to get my new nvidia card woking.  I was pretty happy.  I came back to my comp tonight and I started to have resolution problems with my screen.  I could not get it set to 800X600, just the size below that.  After fussing around with it for awhile i found somewhere that you can fix this problem by running:

sudo dpkg-reconfigure -phigh xserver-xorg

And there went all of my settings in /etc/X11/xorg.conf  Now after fooling around with my touch screen and /etc/X11/xorg.conf it does not seem to work on what I use to have before:

Section "InputDevice"
	Identifier	"EETI"
	Driver		"usbtouchscreen"
	Option		"Device"	"dev/input/event4"
	Option		"Parameters" 	"/etc/egalax.cal"
	Option		"ScreenNo"	"0"
EndSection

When I leave option "device"        ""          blank it works, but as soon as i tell it event 4, i load a black screen on reboot.  
Does anyone Have any ideas?
Thanks

---

### Post by sirgogo on 2007-10-02
Well, I'm pretty sure the black screen on reboot means theres a problem with starting the X.

I'm thinking you should leave the screen so that it works with a low resolution and touch screen, but then edit the "Screen" section of the xorg.conf file so that it looks something like this: (to fully access the file you need to log in as root)


```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

All those subsections are really unnecessary, but whatever.

Give it a shot and let me know how it goes. ;)

---

### Post by endlessurf on 2007-10-03
Hey thanks for the reply, most of the time i just post and nothing comes of it or i just end up posting to myself over and over until i get it worked out.  I managed to find out what was wrong, it was the interface between my chair and my computer.  I got my stuff up and running, thank you though

---

### Post by endlessurf on 2007-10-04
need help making my usb mouse stay on an event vs randomly being assigned a new event number every time i sign on.  I've look around and have not foiund much so anything would hellp

---

### Post by endlessurf on 2007-10-04
bump

---

### Post by endlessurf on 2007-10-04
bump with arms behind the back typing

---

### Post by endlessurf on 2007-10-04
bounce

---

### Post by endlessurf on 2007-10-05
bump

---

### Post by endlessurf on 2007-10-05
bump

---

### Post by endlessurf on 2007-10-09
bumpage

---

### Post by llamakc on 2007-10-09
Give details. Your rig, your mouse, the output of `sudo lsusb`, and how did you discover you're getting a different event#. What other USB devices do you have on the machine? You know, details.

---

### Post by endlessurf on 2007-10-09
thanks for the reply, i just said it was a mouse in order for someone to help me.  It is realy a touchscreen that i have config and it works most of the time.  My issue is that in my xorg.conf file i have something that says "dev'/input/event3"  this event should relate to my touchscreen.  but as soon as i attach other usb devices the touch screen is sometimes assigned event 3.  I want to keep the event of the touchscreen the same so i don't have this problem
thanks again for the reply

---

### Post by endlessurf on 2007-10-10
bump

---

### Post by endlessurf on 2007-10-10
bump bump bump

---

### Post by endlessurf on 2007-10-10
bump

---

### Post by llamakc on 2007-10-10
Start a new thread with the REAL details of your problem and please stop bumping the threads so often.

---

### Post by endlessurf on 2007-10-10
I currently am running a gigabyte s series w/ 64 intel.  I am using 64 feisty.  I have a nvidia 8500 gt set up and I am using a touchscreen.  Everything is working great provided I do not have any other usb devices besides my touchscreen plugged into the computer.  By the way the touchscreen is usb.  In my /etc/X11/xorg.conf i have a line that references the event and my touch screen:

Section "InputDevice"
      Identifier "EETI"
      Driver     "egalax"
     **Option      "Device"    "/dev/input/event3"**
      Option     "Parameters" "/etc/egalax.cal"
#      Option     "ScreenNo"   "0"

 EndSection

The issue is that when i add other usb devices my touchscreen is not assigned event 3 but some random event.  I would like my usb touch screen to work all of the time and not have to boot the computer and put in usb devices after the desktop shows up.

Here is some other info that might help someone help me:

cat /proc/bus/usb/devices
T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0eef ProdID=0001 Rev= 1.00
S:  Manufacturer=eGalax Inc.
S:  Product=USB TouchController
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbtouchscreen
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=5ms

cat /proc/bus/input/devices
I: Bus=0003 Vendor=0eef Product=0001 Version=0100
N: Name="eGalax Inc. USB TouchController"
P: Phys=/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 event3 ts1 
B: EV=b
B: KEY=400 0 0 0 0 0
B: ABS=3

any help would be nice.  Thanks

---

### Post by endlessurf on 2007-10-11
bump again

---

### Post by endlessurf on 2007-10-11
bump

---

### Post by endlessurf on 2007-10-11
bumpage

---

### Post by endlessurf on 2007-10-11
bump

---

### Post by llamakc on 2007-10-11
Have you considered the kernel mailing list?

---

### Post by endlessurf on 2007-10-12
kernal mailing list......???????  I'm have now clue what that is or how that will help me.  If you can give me more information that will be nice.  thanks

---

### Post by loell on 2007-10-12
can you also post the output when other usb devices are present? and see what happens, on why it gets assigned differently?

---

### Post by endlessurf on 2007-10-12
you want me to cat /proc/bus/input/devices
or do the same but for usb

---

### Post by loell on 2007-10-12
yeah, same procedure like you did before, but with other usbs present at boot time.

---

### Post by Sef on 2007-10-12
Moved to X86 64-bit forum.

---

