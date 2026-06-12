---
title: "Macbook touchpad cursor moving &quot;in steps&quot;"
date: 2008-05-31
forum: Apple Hardware Users
---

### Post by attenpeter on 2008-05-31
Hi,

I already accidently posted a similar post in the Apple Intel Archive (I was directly linked to it and didn't realize it was an archive... sorry for that) and was suggested to search this forum, as a few people had similar issues. I couldn't find anything useful and so I thought it's a good idea to post it once again here :)

If I try to configure my touchpad behaviour I always notice the following no matter what I change: The cursor in mac os smoothly moves in a straigt line from one edge to the other if I drag my finger diagonally... In ubuntu, the cursor first moves right, then down, then right, then down, like drawing small steps... it's really annoying and makes navigation in a menu quite a task...

Here are some pictures to clarify: ;)

mac os cursor movement:
```
\
 \
  \
```

ubuntu cursor movement:
```
|
 -
  |
   -
```

I don't know if this is a driver or configuration issue... I used (and tried to tweak) the configuration from this link: [https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-b746291600b14e15576a94b5a5ae7d325138b8cb](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-b746291600b14e15576a94b5a5ae7d325138b8cb)

Anyone knows how to solve this? Or, as an alternative, anyone with a santa rosa c2d macbook (macbook3,1) who doesn't have this problem willing to post his/her xorg.conf?

cu,
peter

---

### Post by ditsch on 2008-05-31
Hm, I am using this one on my MBP Santa Rosa (I think the touchpad is equal to those in the Macbooks):

```
Section "InputDevice" 
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
	 Option		"SendCoreEvents"	"true"
        Option "Device" "/dev/input/touchpad"
        Option "Protocol" "auto-dev"
        Option "VertScrollDelta" "20"
        Option "HorizScrollDelta" "350"
        Option "VertTwoFingerScroll" "true"
        Option "HorizTwoFingerScroll" "true"
        Option "FastTaps" "false"
        Option "TapButton2" "3"
        Option "AccelFactor" "0.3"
        Option "SHMConfig"  "on"
EndSection
```

Hope this helps...

---

### Post by attenpeter on 2008-06-01
Hi,

I'll try this tomorrow and see if it works, although I'm quite sceptical as it is similar to my config...

cu,
peter

---

### Post by attenpeter on 2008-06-02
Well, unfortunately, the cursor movement still is like that...

---

### Post by attenpeter on 2008-06-04
nobody else? At least confirmations of this problem?

---

### Post by cyberdork33 on 2008-06-04
> **attenpeter said:**
> nobody else? At least confirmations of this problem?
search in the forum archive as I am sure that someone has reported something similar before. It seems that adjusting values in the xorg.conf tends to fix it though.

---

### Post by tsnorder on 2008-06-16
hi there,

I have a macbook3,1 and Im experiencing the exact same problem as attenpeter.

Tore

---

### Post by attenpeter on 2008-06-16
> **cyberdork33 said:**
> search in the forum archive as I am sure that someone has reported something similar before. It seems that adjusting values in the xorg.conf tends to fix it though.

I'm sorry, I searched a lot (here and google), tried A LOT of parameter tuning... The problem still exists :(

My guess is that it is a macbook3,1 issue as other macbooks don't seem to be affected...

I don't know, just a wild guess (I'm quite desperate), but the XNU kernel (mac os X kernel) is said to be open source; wouldn't it be possible to understand how the touchpad driver there works and implement/port it to a linux kernel? Or does apple use "binary driver modules" that prevent that?
That is, IF this is a driver issue.....

---

### Post by tsnorder on 2008-06-16
I have also done quite a lot of synaptics tweaking with no solution. I am no synaptics guru, but I am feeling more and more confident that the problem might lay with the appletouch driver somehow. I have tried tweaking some params in that driver without really knowing too much about what I am doing, and with no results. It may be a problem with the way the driver calculates the current position.

---

### Post by tiagobt on 2008-06-19
Same problem here. Did anyone manage to fix it? Did you find values that work well in xorg.conf?

Thanks,
Tiago

---

### Post by undertakingyou on 2008-06-20
I was having the same issues but noticed that when I did a fresh install the issue wasn't there so, I selectively edited my xorg.conf to get what I feel is a smooth scroll and tap-drag speed etc.  Here is my section:
```

Section "InputDevice"
    Identifier	"Synaptics Touchpad"
    Driver	"synaptics"
    Option	"SendCoreEvents"	"true"
    Option	"Device"	"/dev/psaux"
    Option	"Protocol"	"auto-dev"
    Option	"HorizEdgeScroll"	"0"
    Option      "VertEdgeScroll"    "0"
    Option      "TapButton1"        "1"
    Option      "TapButton2"        "3"
    Option      "TapButton3"        "2"
    Option      "VertTwoFingerScroll"   "1"
    Option      "SHMConfig"         "on"
EndSection

```
This makes it so you use two fingers for right click and three fingers for middle click.  It also adds the two finger scroll.
Now you could add the lines for Horizontal two finger scroll etc, but I find that one rather annoying so I don't do it.  
Anyways, I hope that helps.

---

### Post by tiagobt on 2008-06-20
Actually, I've just installed Ubuntu, so I don't think reinstalling will help much. My xorg.conf is very similar to yours. Are those the only settings you're using? Currently, mine looks as follows:

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "true"
        Option          "LeftEdge"              "10"
        Option          "RightEdge"             "1200"
        Option          "TopEdge"               "10"
        Option          "BottomEdge"            "370"
        Option          "FingerLow"             "10"
        Option          "FingerHigh"            "20"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "220"
        Option          "SingleTapTimeout"      "100"
        Option          "MaxDoubleTapTime"      "180"
        Option          "LockedDrags"           "off"
        Option          "MinSpeed"              "1.10"
        Option          "MaxSpeed"              "1.30"
        Option          "AccelFactor"           "0.08"
        Option          "TapButton1"            "1"
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"
        Option          "RTCornerButton"        "0"
        Option          "RBCornerButton"        "0"
        Option          "LTCornerButton"        "0"
        Option          "LBCornerButton"        "0"
        Option          "VertScrollDelta"       "20"
        Option          "HorizScrollDelta"      "50"
        Option          "HorizEdgeScroll"       "0"
        Option          "VertEdgeScroll"        "0"
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1"
EndSection
```

Are you using the default values for speed and acceleration?

Thanks,
Tiago

---

### Post by attenpeter on 2008-06-20
undertakingyou, what model do you have?

---

### Post by cyberdork33 on 2008-06-23
> **attenpeter said:**
> undertakingyou, what model do you have?
he has a MacBook3,1

---

### Post by kosumi68 on 2008-06-25
Are you using appletouch? There is a chance that you are running the inferior usbhid. You can check which input device synaptics is using with

```
grep /input /var/log/Xorg.0.log
```

then match it against the output of dmesg:

```
dmesg | grep /input
```

---

### Post by tiagobt on 2008-06-25
I think I'm already using appletouch. I'm pasting the outputs below.

grep /input /var/log/Xorg.0.log
```
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(**) Option "Device" "/dev/input/mice"
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
```

dmesg | grep /input
```
[   64.458555] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   77.025891] input: PC Speaker as /devices/platform/pcspkr/input/input1
[   77.065241] input: Power Button (FF) as /devices/virtual/input/input2
[   77.148752] input: Lid Switch as /devices/virtual/input/input3
[   77.180803] input: Power Button (CM) as /devices/virtual/input/input4
[   77.245342] input: Sleep Button (CM) as /devices/virtual/input/input5
[   77.525988] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   78.275829] input: appletouch as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.1/input/input7
[   78.316148] input: Apple Mac mini infrared remote control driver as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input8
[   78.644790] input: Apple Computer Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input9
[   78.707592] input: Apple Computer Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.2/input/input10
[   78.905036] input: HID 05ac:1000 as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.0/input/input11
[   78.976567] input: HID 05ac:1000 as /devices/pci0000:00/0000:00:1d.3/usb4/4-1/4-1:1.1/input/input12
[   79.577375] input: applesmc as /devices/platform/applesmc.768/input/input13
```

---

### Post by undertakingyou on 2008-06-25
> **attenpeter said:**
> undertakingyou, what model do you have?

I do have a MacBook Pro Third Generation.  (macbookpro3,1).  Those are the only settings that I have in my xorg and it works fine.  Way better than when I had that huge list of stuff.

---

### Post by kosumi68 on 2008-06-25
So it seems. And you are able to run gsynaptics and everything, I take it. I would start by stopping mouseemu and pommed if you have them, then do

```

sudo rmmod appletouch

```

check the output of dmesg|tail, then do

```

sudo modprobe appletouch

```

and check dmesg|tail again, to make sure it really is the appletouch driver that claims the device. After reapplying the appletouch driver, you need to logout (restart X).

It have doubts this will work, but it wont hurt; I had problems getting my new bcm5974 driver for the MBA working because of the order the drivers were initialized.

---

### Post by tiagobt on 2008-06-25
kosumi68,

Thanks for the help. Just after I ran "rmmod appletouch," the cursor froze. Running "modprobe appletouch" made the touchpad start working again. I guess that proves I'm actually using appletouch. I have never used GSynaptics. I guess I should give it a try.

You know what, I think undertakingyou is right. I tried using the simple configuration in xorg.conf and the touchpad is performing better now. The motion "in steps" can still be noticed, but at least I have more control now.

Tiago

---

### Post by kosumi68 on 2008-06-29
I am still wondering about this; if your mouse is a geyser-like device, and for some reason the mouse is claimed by usbhid (there are two devices claimed according to the output you provided), then this might still be a module initialization race: appletouch might not have set the right protocol mode of the device. Two things to try:

1. Report the output of these commands

```

uname -r
lsusb

```

Given the device codes, I can check if it is a geyser device and how the usbhid module handles the mouse interface of that device.

2. Change the initialization order usbhid<->appletouch

/etc/modprobe.d/blacklist:
```

blacklist usbhid

```

/etc/modules, after appletouch:
```

usbhid

```

Make sure you spell the module names correctly: failure to load usbhid will make your keyboard not working -> booting from rescue disk. :)

---

### Post by tiagobt on 2008-06-30
OK, one more try!

The outputs are the following:

uname -r
```
2.6.24-19-generic
```

lsusb
```
Bus 005 Device 003: ID 05ac:8501 Apple Computer, Inc. Built-in iSight [Micron]
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 003: ID 05ac:8205 Apple Computer, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 05ac:8240 Apple Computer, Inc. IR Receiver [build-in]
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 05ac:021a Apple Computer, Inc.
Bus 001 Device 001: ID 0000:0000
```

I added the line "blacklist usbhid" to the end of the file /etc/modprobe.d/blacklist, but I'm not sure what to change on /etc/modules. The file does not include "appletouch" or "usbhid". Should I add both to the end of the file?

Thanks once again,
Tiago

---

### Post by cyberdork33 on 2008-06-30
> **tiagobt said:**
> I'm not sure what to change on /etc/modules. The file does not include "appletouch" or "usbhid". Should I add both to the end of the file?

Yes, just make sure that usbhid is on a line after appletouch.

---

### Post by tiagobt on 2008-07-01
I tried to do that, but unfortunately the result was the same. Thanks for trying to help anyway.

---

### Post by tiagobt on 2008-07-06
Do you think the following patch might help?

[http://www.jmadden.eu/index.php/2007/04/09/macbook-synaptics-touchpad/](http://www.jmadden.eu/index.php/2007/04/09/macbook-synaptics-touchpad/)

---

### Post by kosumi68 on 2008-07-06
Reading the patch, it seems it has already been applied some time ago, unfortunately.

---

### Post by tiagobt on 2008-07-16
I've been trying different options in Xorg.conf and I guess I found a configuration that works fairly well to me. I'll post it in case someone would like to try it:

```
Section "InputDevice"
	# Basic settings
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"		"true"
	# Trackpad edges
	Option		"LeftEdge"		"10"
	Option		"RightEdge"		"1200"
	Option		"TopEdge"		"10"
	Option		"BottomEdge"		"370"
	# Tap buttons
	Option		"TapButton1"		"1"
	Option		"TapButton2"		"3"
	Option		"TapButton3"		"2"
	# Corner taps (disabled)
	Option		"RTCornerButton"	"0"
	Option		"RBCornerButton"	"0"
	Option		"LTCornerButton"	"0"
	Option		"LBCornerButton"	"0"
	# Two-finger scroll
	Option		"VertTwoFingerScroll"	"on"
	Option		"HorizTwoFingerScroll"	"on"
	Option		"VertScrollDelta"	"20"
	Option		"HorizScrollDelta"	"50"
	# Edge scroll (disabled)
	Option		"HorizEdgeScroll"	"off"
	Option		"VertEdgeScroll"	"off"
	# Locked drag (disabled)
	Option		"LockedDrags"		"off"
	# Finger pressure
	Option		"FingerLow"		"10"
	Option		"FingerHigh"		"20"
	# Pointer speed and acceleration
	Option		"MinSpeed"		"0.15"
	Option		"MaxSpeed"		"1.00"
	Option		"AccelFactor"		"0.15"
	# Single tap
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"220"
	Option		"SingleTapTimeout"	"100"
	# Double tap
	Option		"MaxDoubleTapTime"	"220"
EndSection
```

The trackpad behavior should be similar to the one in Mac OS X. At least I'm happy with the results now.

---

### Post by babyhuey on 2008-07-20
I have this problem as well. Overall touchpad movement is not that smooth.

---

### Post by tomrshl on 2008-08-18
Sorry to bring up an old thread, but as I'm having the exact same problem...
Think I've got a Macbook Pro 3,1 and the cursor is moving just as described in the first post. It's annoying because I have to be with a mouse to use, for example, the selection tools in GIMP.
It moves sort of like it wants to go in a straight vertical/horizontal line as much as possible. It doesn't like going diagonal slowly.
So if anyone ever solved this problem, I'd like to know.
Thanks

---

### Post by hanzomon4 on 2009-06-02
> **tiagobt said:**
> Same problem here. Did anyone manage to fix it? Did you find values that work well in xorg.conf?

Thanks,
Tiago

You may have conflicting settings... Make sure you don't have the touch pad configured in xorg.conf and hal fdi

---

### Post by tiagobt on 2009-06-03
> **hanzomon4 said:**
> You may have conflicting settings... Make sure you don't have the touch pad configured in xorg.conf and hal fdi

Actually, my xorg.conf has nothing related to Synaptics or the touchpad. All my touchpad settings are in /etc/hal/fdi/policy/appletouch.fdi.

---

### Post by dman777 on 2009-06-03
Xorg 1.5 and greater no longer depends on Xorg.conf. (well, unless you use nvidia but still...for touch pad Xorg uses HAL). What you need to do is this:
Install Xorg 1.5 or greater
Install Synaptics Xfree86 driver
Run nvidia-xconfig to get a fresh xorg.conf
Go into xorg.conf and TAKE out any statement with INPUT...this would be the Section "InputDevice" and in the 2 inputdevices in the Section "Server".
Then copy the Synaptics template setting from /usr/share/hal/fdi/policy/ to /etc/hal/fdi/policy/. Edit the file to your likeings.

Restart Hal and X and you'll be good to go!

NOTE: I don't know about appletouch(or whatever) driver, but if it's a Synaptics pad then just use Synaptics driver.

---

### Post by tiagobt on 2009-06-04
I tried the steps you mentioned, getting the following results:

> **dman777 said:**
> 
Install Xorg 1.5 or greater

Ubuntu comes with Xorg 1.6.0, so there was nothing to install.

> **dman777 said:**
> 
Install Synaptics Xfree86 driver

Ubuntu comes with Synaptics 0.99.3, so there was nothing to install.

> **dman777 said:**
> 
Run nvidia-xconfig to get a fresh xorg.conf

I have a MacBook 2,1, which uses Intel GMA 950 for graphics. Therefore, the application nvidia-xconfig is not installed. Should I install it anyway?

> **dman777 said:**
> 
Go into xorg.conf and TAKE out any statement with INPUT...this would be the Section "InputDevice" and in the 2 inputdevices in the Section "Server".

My xorg.conf has no input statements, as you can see below:
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

> **dman777 said:**
> 
Then copy the Synaptics template setting from /usr/share/hal/fdi/policy/ to /etc/hal/fdi/policy/. Edit the file to your likeings.

I was a little confused about this step. There are two folders inside /usr/share/hal/fdi/policy: 10osvendor (several FDI files for different hardware) and 20thirdparty (files 10-wacom.fdi and 11-x11-synaptics.fdi). And there are two files inside /etc/hal/fdi/policy: appletouch.fdi (my touchpad custom settings) and preferences.fdi. What files should I copy? Where should I place them?

Thanks for the help,
Tiago

---

### Post by dman777 on 2009-06-05
First thing is remember that we are going to try and abandon the appletouch software all together and just use the Xfree version of Synatpics drivers.(You still get multi touch).

I think the root of your problem is the Synaptics driver. There are 2 kinds: 1) open source and closed source. Use the open source one- xf86-input-synaptics.

In addition, in your kernel make sure evdev support is enabled. I would suggest, as we are problem shooting... to disable the appletouch pad driver. Why use this if we are going to use the Xfree Synaptics one instead? Also, remember...any driver built into the kernel will trump any external loaded driver. Although this may not matter to much since Xorg is useing the Synaptics driver only...not the system. Still, we're trouble shooting. I'll let it be your call. But I suspect the kernel appletouch driver could could be interfering. 

See if these things work. If not try this in addditon:

Ok, I thought you had a nvidia card. In this case, try renameing your xorg.conf to something like xorg.conf_NoUse. In otherwards, lets try to see if we can get away without using xorg.conf.

HAL uses both /usr/share/hal/fdi/10osvendor and /etc/had/fdi/policy. Basically, ether or can be used. But whatever is in the later directory takes precedence of whatever is in the earlier directory. So use /etc/hal/fdi/policy. Also, when you up date Hal the config file in /etc/hal/fdi/policy will not get written over. 

There should be a config file in /usr/share/hal/fdi/10osvendor/11-x11-synaptics.fdi. copy that over to the /etc/hal/fdi/policy/11-x11-synaptics.fdi. Then edit it and uncomment what you want to be activated. Rename any appletouch files in /etc/hal/fdi/policy to something so they won't get used. When ever you are done editing a HAL fdi file you have to restart HAL and X.

---

### Post by cyberdork33 on 2009-06-05
appletouch and synaptics are not the same thing. you cannot trade one for the other.

appletouch is the kernel driver for older mac touchpads. it is the part of the code that make your hardware actually do something. The hardware that uses this driver (and this is the only driver for linux for them) is not "multitouch". This does not mean you cannot do actions with more than one finger, it means that the hardware is incapable on independently tracking multiple touches on the pad at once. You can still two-finger scroll, two-finger tap, etc, just like on older PC touchpads. On newer Mac touchpads, this driver is replaced by the bcm5974 driver and they are true"multitouch" touchpads capable of tracking several (11?) different touches at once. This hardware is what allows some of the more cool gestures like rotation, and zoom.

now then, the Xorg driver that turns the data from the kernel drivers into something useful that you can do on the screen is the synaptics driver. This is the driver that translates: "two fingers moving vertically" to "scroll the active window vertically". It is the same driver that you would use for both of the hardware types mentioned above.

---

### Post by dman777 on 2009-06-09
This is issue does not exists on PC's, so is the issue from the xorg synaptics driver interacting with the kernel appletouch driver?

Also, is Macbook touchpad made by Synaptics? If so, then can kernel appletouch driver be bypassed and a pc synaptics driver be used? Logic being, if trackpad is made by the synaptics then there shouldn't be much diff. between the hardware.

---

### Post by cyberdork33 on 2009-06-10
> **dman777 said:**
> This is issue does not exists on PC's, so is the issue from the xorg synaptics driver interacting with the kernel appletouch driver?I would guess it is a bug with using the appletouch driver with specific hardware.

> Also, is Macbook touchpad made by Synaptics? If so, then can kernel appletouch driver be bypassed and a pc synaptics driver be used? Logic being, if trackpad is made by the synaptics then there shouldn't be much diff. between the hardware.

I am not sure who makes them. The newer ones are controlled with a broadcom chip. However, even if it was made by synaptics, Apple likely has their own software interface for it that is unique.

---

### Post by thecheeks on 2009-06-11
Finally got the trackpad with better sensitivity settings, however I am too having the 'movement step' problems too. Makes it hard to hit a radio button or click something specific since it'll literally jump to the side rather than diagonal movements.

---

### Post by NoBugs! on 2009-06-20
I think this may be a hardware problem.
If you start up holding alt/option, the boot select screen has the same cursor jumping problem, and no operating system is started yet.
It seems both Mac os and Ubuntu 9.04 minimize the jumping mouse cursor through their builtin software drivers.

---

### Post by tiagobt on 2009-06-21
> **NoBugs! said:**
> I think this may be a hardware problem.
If you start up holding alt/option, the boot select screen has the same cursor jumping problem, and no operating system is started yet.
It seems both Mac os and Ubuntu 9.04 minimize the jumping mouse cursor through their builtin software drivers.

Interesting. The problem is very evident in this screen. Do you know what trackpad driver is loaded when you boot holding alt/option? If this is indeed a hardware issue, then Mac OS X seems to do a very good job in minimizing the problem. Maybe there's some chance of improvement in appletouch as well.

---

### Post by tiagobt on 2009-06-28
Do you think I should I file a bug for appletouch? Where should I report the bug?

---

### Post by DTedesco on 2011-10-30
Two years later and the bug still persists (Ubuntu 11.10, MacBook3,1). 
Still no solution?

---

### Post by diddledan on 2011-12-01
*subscribing to replies*

I am having this issue, also, on a MacBook 4,1. Other than the terrible motion of the cursor the trackpad functions perfectly normally. I guess I will need to take a mouse and lapdesk with me wherever I go.

Xorg.0.log reports:

```
$ grep apple /var/log/Xorg.0.log 
[    23.012] (II) config/udev: Adding input device appletouch (/dev/input/event5)
[    23.012] (**) appletouch: Applying InputClass "evdev touchpad catchall"
[    23.012] (**) appletouch: Applying InputClass "touchpad catchall"
[    23.150] (II) Using input driver 'synaptics' for 'appletouch'
[    23.150] (**) appletouch: always reports core events
[    23.160] (--) appletouch: x-axis range 0 - 1215
[    23.160] (--) appletouch: y-axis range 0 - 575
[    23.160] (--) appletouch: pressure range 0 - 300
[    23.160] (--) appletouch: buttons: left double triple
[    23.160] (--) appletouch: invalid finger width range.  defaulting to 0 - 16
[    23.164] (--) appletouch: touchpad found
[    23.164] (**) appletouch: always reports core events
[    23.169] (II) XINPUT: Adding extended input device "appletouch" (type: TOUCHPAD)
[    23.169] (**) appletouch: (accel) MinSpeed is now constant deceleration 2.5
[    23.169] (**) appletouch: MaxSpeed is now 1.75
[    23.169] (**) appletouch: AccelFactor is now 0.149
[    23.169] (**) appletouch: (accel) keeping acceleration scheme 1
[    23.169] (**) appletouch: (accel) acceleration profile 1
[    23.169] (**) appletouch: (accel) acceleration factor: 2.000
[    23.169] (**) appletouch: (accel) acceleration threshold: 4
[    23.169] (II) appletouch: failed to open grail, no gesture support
[    23.169] (--) appletouch: touchpad found
[    23.170] (II) config/udev: Adding input device appletouch (/dev/input/mouse0)
[    23.180] (II) config/udev: Adding input device applesmc (/dev/input/event6)
[    23.180] (II) config/udev: Adding input device applesmc (/dev/input/js0)
```

---

### Post by art_s on 2012-01-09
Same issue - after fixing the responsiveness with FingerLow/FingerHigh settings of synclient I started getting the same problem with 'jumpiness' - it's really hard to point with cursor on something small.

Could that be just another setting of synclient?

---

### Post by gonum09 on 2012-05-03
Does anyone have a fix for the pointer not going diagonally properly? If so please share.

I have a MacbookPro 3,1 and haven't used ubuntu for a while now as the last few versions the cursor always used to freeze which made Ubuntu unusable as I don't carry a mouse with my laptop.

It's nice that it actually works in 12.04 but the diagonal problem really spoils it so much so I can't see myself continuing to use Ubuntu until I can fix this.

Ive followed the thread through and I can adjust the feel of the cursor but it still alway moves diagonally in 90 degree turns.

---

### Post by art_s on 2012-05-03
See if this helps

[http://askubuntu.com/questions/80488/sluggish-unresponsive-trackpad-on-pre-unibody-macbook-pro](http://askubuntu.com/questions/80488/sluggish-unresponsive-trackpad-on-pre-unibody-macbook-pro)

---

### Post by gonum09 on 2012-05-03
> **art_s said:**
> See if this helps

[http://askubuntu.com/questions/80488/sluggish-unresponsive-trackpad-on-pre-unibody-macbook-pro](http://askubuntu.com/questions/80488/sluggish-unresponsive-trackpad-on-pre-unibody-macbook-pro)

Thanks,

I tried synaptics.conf but no difference. Previously I had only been editing the xorg.conf

It was actually that thread that brought me to this one, if you read the edited note at the bottom of the posts.

I initially didn't try it, as the problem I have is the track pad cursor moving "in steps", think an etchasketch with poor resolution or drawing a circle with your finger and seeing a square.

---

### Post by art_s on 2012-05-03
> **gonum09 said:**
> 
I initially didn't try it, as the problem I have is the track pad cursor moving "in steps", think an etchasketch with poor resolution or drawing a circle with your finger and seeing a square.

Sorry to hear that. To be frank I never fixed the jumping issue, and then macbook died, rendering the problem irrelevant :)

Hope you'll be able to fix it!

---

### Post by gonum09 on 2012-05-03
But you already know that, i'll try again..... damn my slow typing you replied before  I did

---

### Post by gonum09 on 2012-05-03
Its just strange, i'm sure I never had this problem when I used fedora or when I switched to ubuntu back in 2009. Maybe my memory is just faded. I haven't really used ubuntu linux that much.

---

### Post by gwjvan on 2012-05-12
I have a Powerbook5,8-- the last 15" G4 laptop they made. I have this same issue. I'm assuming that my hardware is similar to the early Intel MacBooks.

Here's an example of me drawing a spiral on the trackpad in mtPaint (without looking at the screen):

[IMG]http://i1058.photobucket.com/albums/t402/gwjvan/trackpad_spiral_example.gif[/IMG] 


As you can see, the larger/faster the movement, the more it registers diagonals. However, for precision movements, it doesn't work very well. It is okay for general use, but for some precision design work (or precision interface interaction) it becomes annoying.

I'm interested in solving this issue as well

---

### Post by gwjvan on 2012-05-14
Summary question: Is there a way to download old .ko files from ubuntu somehow? I know you can find at old packages, but I can't see to find old drivers? Is there a way to find/download an older version of appletouch.ko from a previous ubuntu version?


Basically, I'm wondering if an older version of appletouch might work (at least for my system).

I haven't looked that deeply into it, but a first thought is that it considers subtle movements to be noise. If I can lower the threshold for that, it might work a little better. 

I tried compiling the driver, but I haven't had success yet... so I am not yet able to tweak the source code (working on it).

A thought I had was that maybe an older version of the driver addressed this setting, and the newer version simply fixed a problem for someone else's touchpad (while reducing the sensitivity on others).

---

### Post by gwjvan on 2012-05-14
Okay, just changing a couple of things in appletouch.c improves cursor movement


Two variables (and their default values):
 
   #define ATP_FUZZ	16
 
   #define ATP_THRESHOLD	 5


When I changed the values to:
  
   #define ATP_FUZZ	0
 
   #define ATP_THRESHOLD	 3
 
 
It now behaviors better. Here are some things I drew in mtpaint. The first in each pair is with default appletouch, the second in each pair is after the above tweak. There is an improvement, however, it seems appletouch is still trying to correct my movements a little. Sometimes it doesn't register small movements (sometimes the cursor doesn't move when starting slowly), and sometimes it still has a subtle "stair" like effect when moving diagonally. Your own trackpad might need different settings. (And there is some more tweaking I'd like to do on the driver to stop it from ignoring some of my finger movements)
 
Spiral pre-tweak:
 [IMG]http://i1058.photobucket.com/albums/t402/gwjvan/trackpad_spiral_example.gif[/IMG]

Spiral after tweak:
[IMG]http://i1058.photobucket.com/albums/t402/gwjvan/trackpad_spiral_example_after_tweak.png[/IMG]


Scribbles pre-tweak:
[IMG]http://i1058.photobucket.com/albums/t402/gwjvan/trackpad_scribbles_pre_tweak.gif[/IMG]

Scribbles after-tweak:
[IMG]http://i1058.photobucket.com/albums/t402/gwjvan/trackpad_scribbles_after_tweak.gif[/IMG]

---

### Post by gwjvan on 2012-05-15
And actually... I want to point out that the touchpad behaves this way in Mac OS X, too..... (see images below)

It seems that Apple's solution to this issue was to simply turn the sensitivity way down. The images below were generated with similar-sized finger movements as the ones in my previous post, but notice how much smaller the spiral is (drawn at the same slow speed as above). And notice the subtle "stair" like effect during diagonal movements. Apple seems to have just slowed the cursor movement down more on slow touchpad gestures to reduce the appearance of the "step" effect.

Also, one other thing stuck out: The mac os x cursor seems to lag behind the touchpad gestures. I'm guessing that Apple's driver has a bit of a delay in order to calculate the average of the movements that just took place before applying them to the screen (to cancel out weird jumping, as sometimes seen with the appletouch driver).
 
 
Slow diagonal down the touchpad, drawn in Mac OS X. Notice the subtle "stair" like effect:
[IMG]http://i1058.photobucket.com/albums/t402/gwjvan/mac_os_x_diagonal.gif[/IMG]
  
 
Spiral drawn in Mac OS X:
[IMG]http://i1058.photobucket.com/albums/t402/gwjvan/mac_os_x_spiral.gif[/IMG]
 
 
Back to linux: 

If I disable multitouch reporting in the driver, I am able to set the ATP_THRESHOLD     to 1, (otherwise it reports single-finger gestures as multi-finger). With ATP_THRESHOLD     set to 1, I see more accurate touchpad results. However, the cursor jumps around occasionally. I wonder how difficult it would be to program in a delay to calculate smoother movement with a lower threshold (or if there is some tool/driver/synaptics setting out there that already does this?).

.

---

### Post by gonum09 on 2012-05-23
How do I make these changes to appletouch.c ?

Thanks

---

### Post by gwjvan on 2012-05-24
If the following information doesn't make sense, or you run into trouble, I'll be posting a more detailed post later. Basically, you'll have to compile the driver yourself. Short version:

You will need to get the newest appletouch.c from the kernel tree on kernel.ubuntu.com:
drivers > input > mouse > appletouch.c

I used the Makefile from appletouch-0.08.tar.bz2 at the bottom of the page of:
[http://www.popies.net/atp/](http://www.popies.net/atp/)
(maybe not necessary to use this specific Makefile, but it is the way I got appletouch compiling to work)


There were roadblocks I ran into when trying to compile the driver. I wrote some of them in a text file for reference, and didn't log others. I'm interested in (maybe?) submitting changes to this driver. I'm going to reinstall ubuntu so I can start fresh and log what I did.


EDIT: I originally had kernel.org as the place to get appletouch.c, however, that doesn't work. I needed the source file from Ubuntu Precise (you'll need to match your own version)

---

### Post by gwjvan on 2012-05-27
Here is what I did to compile and make appletouch functional. I'm still learning, so if there is a better way to do any of this, please feel free to correct me. Also, there is more tweaking I'd like to do, but these are the basic instructions for you to be able to experiment. According to appletouch.c, appletouch applies to the following Mac laptops:[INDENT] /* PowerBooks Feb 2005, iBooks G4 */
/* PowerBooks Oct 2005 */
/* Core Duo MacBook & MacBook Pro */
/* Core2 Duo MacBook & MacBook Pro */
/* Core2 Duo MacBook3,1 */
[/INDENT]Summary: Use the original appletouch make file (from the authors), with the newest appletouch.c (from the kernel tree), changing a few values.



1. Get the Makefile. Download the most recent appletouch package from:[INDENT][http://www.popies.net/atp/index.html](http://www.popies.net/atp/index.html)
[/INDENT]The most recent one I see today is appletouch-0.08.tar.bz2. It is outdated, but I'm only using the Makefile from this. I'm going to extract "Makefile" to ~/appletouch/ for this example.
  
  
 
2. Download the appletouch.c from the kernel tree (kernel.ubuntu.com/git) which matches your kernel version. In my case, I'm downloading from the Precise tree:
    kernel.ubuntu.com/git --> projects (top link) --> ubuntu/ubuntu-precise.git > tree (upper left hand link) >  drivers > input > mouse > appletouch.c : raw

   Direct link to appletouch.c's directory in Precise's tree, as of today (If you have a different kernel, or this link doesn't work, you'll need to find it manually):[INDENT][http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=tree;f=drivers/input/mouse]("http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=tree;f=drivers/input/mouse;h=4d7945a882f0de000e0350cfcbfa8904f6b7d793;hb=HEAD")
[/INDENT]From here, click the "raw" link to the right of "appletouch.c" to download the raw file. Put this file into ~/appletouch/   

   Ubuntu seems to have named the raw file "drivers_input_mouse_appletouch.c". If yours downloads with that filename, rename it to "appletouch.c"
  
  
  
3. We should now have the directory ~/appletouch with the following 2 files in it:[INDENT]     appletouch.c (from the kernel tree)
    Makefile (from the appletouch website)
[/INDENT]4.  Install kernel headers (if you don't already have them installed):[INDENT]       sudo apt-get install Linux-headers-$(uname -r)
[/INDENT]5.  Modify appletouch.c with new sensitivity values. In my case (PowerBook5,8 ) I changed:[INDENT]        #define ATP_FUZZ 16

       #define ATP_THRESHOLD 5
[/INDENT]to[INDENT]        #define ATP_FUZZ 0

       #define ATP_THRESHOLD 3
[/INDENT]6. Compile appletouch.c. Open up a terminal and run the following commands:[INDENT]          cd ~/appletouch
         make
[/INDENT]7. Disable current appletouch (with rmmod) and test your new appletouch driver (with insmod) to see if the settings work:[INDENT]      sudo rmmod appletouch
     sudo insmod appletouch.ko
[/INDENT]8. If you are not satisfied with the touchpad behavior, go back to step 5 and adjust settings.
   If you want to go back to default appletouch in the mean time (if your new settings are unusable, for example), you can unload your new driver, and insert the original with:[INDENT]      sudo rmmod appletouch
     sudo modprobe appletouch
[/INDENT]9. If this works for your machine, backup your original appletouch driver:[INDENT]       sudo mv /lib/modules/$(uname -r)/kernel/drivers/input/mouse/appletouch.ko /lib/modules/$(uname -r)/kernel/drivers/input/mouse/appletouch_OLD.ko
[/INDENT]10. Make the new driver the default appletouch driver by copying it to the drivers directory:[INDENT]     sudo cp appletouch.ko /lib/modules/$(uname -r)/kernel/drivers/input/mouse/appletouch.ko[/INDENT]

---

### Post by JROxid on 2012-05-31
If you are running a macbook pro 3.1 I advise everyone to do the same as gwjvan and do the following:
Add:
synclient FingerLow=1; synclient FingerHigh=10

to the startup (test this out in the terminal, other values might work better for you)

It gave me a very accurate tracking


@gwjvan Thank you so much for this, I just installed Ubuntu 12.04 and was just about to uninstall it because of the trackpad, i hate things that don't go the way they are supposed to work. Now my trackpad feels natural and I have the great benefits of running a linux machine :)

---

### Post by gwjvan on 2012-05-31
I'm glad it worked for you

Yeah, it is frustrating when basic stuff doesn't work right

---

### Post by onceler on 2012-06-02
Great instructions gwjvan and JROxid! They are straightforward and readable and, more importantly, effective at making the touchpad and courser feel definitely more like they did under OS X. However, after doing all this, my two finger scrolling is more elastic. That is, when I push my two fingers along the touchpad, say to scroll up, sometimes what I'm looking at (e.g. Chromium page, emacs, PCManFM) scrolls down when I touch the pad and other times down when I take my fingers off the pad. Had any experience with this? 


Setup

Ubuntu 12.04 LTS: 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686 i686 i386 GNU/Linux

appletouch.c found under [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=tag;h=refs/tags/Ubuntu-3.2.0-24.39](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=tag;h=refs/tags/Ubuntu-3.2.0-24.39)

Macbook1,1

---

### Post by gwjvan on 2012-06-14
> **onceler said:**
> Great instructions gwjvan and JROxid! They are straightforward and readable and, more importantly, effective at making the touchpad and courser feel definitely more like they did under OS X. However, after doing all this, my two finger scrolling is more elastic. That is, when I push my two fingers along the touchpad, say to scroll up, sometimes what I'm looking at (e.g. Chromium page, emacs, PCManFM) scrolls down when I touch the pad and other times down when I take my fingers off the pad. Had any experience with this?
 
 
It is doing that for me as well. I don't know how to fix that. Could be a synaptics setting? Or it might be the driver itself, when it switches from multitouch reporting to single touch reporting.
 
 
Also, it seems when the kernel is updated from software updates, the appletouch driver is reset, and step 10 above needs to be done again to get the new driver. (It has done this a couple of times since I wrote the steps above)

---

### Post by WolfieZero on 2012-08-17
Just a massive thank you to gwjvan for that step-by-step guide. It's worked perfectly for my MacBook2,1.

Makes the trackpad workable now.

---

### Post by boneskid1 on 2012-10-31
> **gwjvan said:**
> Here is what I did to compile and make appletouch functional. I'm still learning, so if there is a better way to do any of this, please feel free to correct me. Also, there is more tweaking I'd like to do, but these are the basic instructions for you to be able to experiment. According to appletouch.c, appletouch applies to the following Mac laptops:[INDENT] /* PowerBooks Feb 2005, iBooks G4 */
/* PowerBooks Oct 2005 */
/* Core Duo MacBook & MacBook Pro */
/* Core2 Duo MacBook & MacBook Pro */
/* Core2 Duo MacBook3,1 */
[/INDENT]Summary: Use the original appletouch make file (from the authors), with the newest appletouch.c (from the kernel tree), changing a few values.



1. Get the Makefile. Download the most recent appletouch package from:[INDENT][http://www.popies.net/atp/index.html](http://www.popies.net/atp/index.html)
[/INDENT]The most recent one I see today is appletouch-0.08.tar.bz2. It is outdated, but I'm only using the Makefile from this. I'm going to extract "Makefile" to ~/appletouch/ for this example.
  
  
 
2. Download the appletouch.c from the kernel tree (kernel.ubuntu.com/git) which matches your kernel version. In my case, I'm downloading from the Precise tree:
    kernel.ubuntu.com/git --> projects (top link) --> ubuntu/ubuntu-precise.git > tree (upper left hand link) >  drivers > input > mouse > appletouch.c : raw

   Direct link to appletouch.c's directory in Precise's tree, as of today (If you have a different kernel, or this link doesn't work, you'll need to find it manually):[INDENT][http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=tree;f=drivers/input/mouse]("http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=tree;f=drivers/input/mouse;h=4d7945a882f0de000e0350cfcbfa8904f6b7d793;hb=HEAD")
[/INDENT]From here, click the "raw" link to the right of "appletouch.c" to download the raw file. Put this file into ~/appletouch/   

   Ubuntu seems to have named the raw file "drivers_input_mouse_appletouch.c". If yours downloads with that filename, rename it to "appletouch.c"
  
  
  
3. We should now have the directory ~/appletouch with the following 2 files in it:[INDENT]     appletouch.c (from the kernel tree)
    Makefile (from the appletouch website)
[/INDENT]4.  Install kernel headers (if you don't already have them installed):[INDENT]       sudo apt-get install Linux-headers-$(uname -r)
[/INDENT]5.  Modify appletouch.c with new sensitivity values. In my case (PowerBook5,8 ) I changed:[INDENT]        #define ATP_FUZZ 16

       #define ATP_THRESHOLD 5
[/INDENT]to[INDENT]        #define ATP_FUZZ 0

       #define ATP_THRESHOLD 3
[/INDENT]6. Compile appletouch.c. Open up a terminal and run the following commands:[INDENT]          cd ~/appletouch
         make
[/INDENT]7. Disable current appletouch (with rmmod) and test your new appletouch driver (with insmod) to see if the settings work:[INDENT]      sudo rmmod appletouch
     sudo insmod appletouch.ko
[/INDENT]8. If you are not satisfied with the touchpad behavior, go back to step 5 and adjust settings.
   If you want to go back to default appletouch in the mean time (if your new settings are unusable, for example), you can unload your new driver, and insert the original with:[INDENT]      sudo rmmod appletouch
     sudo modprobe appletouch
[/INDENT]9. If this works for your machine, backup your original appletouch driver:[INDENT]       sudo mv /lib/modules/$(uname -r)/kernel/drivers/input/mouse/appletouch.ko /lib/modules/$(uname -r)/kernel/drivers/input/mouse/appletouch_OLD.ko
[/INDENT]10. Make the new driver the default appletouch driver by copying it to the drivers directory:[INDENT]     sudo cp appletouch.ko /lib/modules/$(uname -r)/kernel/drivers/input/mouse/appletouch.ko[/INDENT]


not working to well.   my powerbook g4 hates the commands 
the raw appletouch.c file you say to download doesn't even have the #define ATP_FUZZ
or the other line that needs to be edited i understand this thread is old but for someone that is still somewhat new to linux your tutorial is crazy as **** to understand so i need to know when you edit those lines is it in the old appletouch.c file the new raw appletouch file or the one that comes with the make file, and the folder /appletouch, you place it in the home folder with the downloads and music folders?

i just need help the cursor moving in steps is unbearable and a major pita to move over links on forums and websites

when i try to compile it terminal tells me no such file or directory it ends with some code and says error 2

---

### Post by Psycam on 2012-11-07
Worked very well for me. Thank you gwjvan!

---

### Post by valroadie on 2012-11-08
Wow! This worked fantastic, thank you gwjvan! I use a macbook 2,1 running Ubuntu 12.04 and it works great, I also want to point out I use synaptics touchpad manager as well and have no problems with it using this config. Yay for smooth mouse control!

---

### Post by gwjvan on 2012-11-15
> **boneskid1 said:**
> not working to well.   my powerbook g4 hates the commands 
the raw appletouch.c file you say to download doesn't even have the #define ATP_FUZZ
or the other line that needs to be edited i understand this thread is old but for someone that is still somewhat new to linux your tutorial is crazy as **** to understand so i need to know when you edit those lines is it in the old appletouch.c file the new raw appletouch file or the one that comes with the make file, and the folder /appletouch, you place it in the home folder with the downloads and music folders?

You use the one from the ubuntu kernel tree, not from the download with the make file. Also, if you are using 12.10, you will need to download the raw appletouch.c file associated with Ubuntu 12.10 listed here:

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-quantal.git;a=tree;f=drivers/input/mouse](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-quantal.git;a=tree;f=drivers/input/mouse)

---

### Post by trolandb on 2012-12-05
Thanks Gwjvan, your solution definitely improves things. Has anyone done any more experimenting with different values in appletouch.c? It's better now but still not as good as windows or osx on the same machine. (2008 macbook)

---

### Post by CPCookieMan on 2013-01-20
Sorry for the bump, but I feel like this is a worthy contribution to a problem people still deal with, even more so now that OSX has abandoned us older MacBook users on Lion or Snow Leopard and we start to yearn for a current operating system.

I would happen to have done a bit of experimenting with the settings. It would seem that setting fuzz to 1 and threshold to 2 calms down the jumpiness a bit.

Using it now. Silky smooth. Thanks guys!

---

### Post by anje84 on 2013-02-21
Hi everybody):P

I'm trying to have a touchpad in my macbook 4.1 core2duo work well but i understand how i do this?excuse me if my language is not very comprehensible im french a i practice  english language very bad.In the moment i'm on debian wheezy and the touchpad is a big problem to have a comfortable use .there a video to my best config :lolflag:[http://www.youtube.com/watch?v=WvFU6MZ5574](http://www.youtube.com/watch?v=WvFU6MZ5574)

I really want to use an linux distro for a personnal use but at the moment it's disagradable.
And the how to in this post is not very clear for me,anybody can help me please?

---

### Post by cmSCIguy on 2013-02-26
I know how to fix the problem of the cursor moving in "steps." I've been running Ubuntu 12.04 on my 2011 Macbook Pro for about a year now and have not been able to configure the trackpad to my liking. When I click (not tap) the trackpad my cursor moves. That's it. Often I end up highlighting things instead of clicking them because the trackpad senses the movement. I've yet to get this worked out. (if anyone has any ideas, let me know! FingerHigh and FingerLow synclient settings help, but don't fix the issue)

Anyway, while doing so I accidentally made my cursor move in steps. Here's how to change the settings.

Open a terminal and type "synclient -l" to bring up a list of current touchpad settings.

Look at your values for HorizHysteresis and VertHysteresis. My current values are 30 and 60, which gives some resistance to diagonal movement. I'm guessing your values are too high and all you need to do is lower them. Here's how

In terminal type
synclient HorizHysteresis=20    and hit enter

Then type
synclient VertHysteresis=30     and hit enter.

That should do it.

---

### Post by anje84 on 2013-03-05
Hi thx to post your synclient config

ived mesured the touchpad of my mac and i have adapted with it's mesure and work better but not perfect. is moving  with a better resolution but always move with a little motion like little stairs and not big stairs ah aha ah! i think it's the way to have  a solution:popcorn:

---

### Post by nortexoid on 2013-04-18
gwjvan, thanks for the help! The touchpad still isn't perfect, but it's WAY better. I also set my FingerLow and FingerHigh settings much lower. Things are certainly usable now.

I see that settings are LOST when the kernel is upgraded. This makes maintaining a usable touchpad a big pain in the butt.

---

### Post by anje84 on 2013-12-03
Hello every body
i found a conf it resolve the problem.
# Example xorg.conf.d snippet that assigns the touchpad driver
# to all touchpads. See xorg.conf.d(5) for more information on
# InputClass.
# DO NOT EDIT THIS FILE, your distribution will likely overwrite
# it when updating. Copy (and rename) this file into
# /etc/X11/xorg.conf.d first.
# Additional options may be added in the form of
#   Option "OptionName" "value"
#
Section "InputClass"
        Identifier "Touchpad"
        Driver "synaptics"
        MatchIsTouchpad "on"
	Option "SHMConfig" "true"
	Option "HorizHysteresis" "50"
        Option "VertHysteresis"  "50"
        Option "MinSpeed" "0.5"
        Option "MaxSpeed" "2.0"
        Option "AccelFactor" "0.5"
 # fix touchpad resolution
        Option "VertResolution" "100"
        Option "HorizResolution" "65"
        Option "HorizTwoFingerScroll" "1"
	Option "VertScrollDelta" "-111"
	Option "HorizScrollDelta" "-111"
	Option "TopEdge" "1374"
	Option "BottomEdge" "1374"
	Option "LeftEdge" "2915"
	Option "RightEdge" "2915"
	Option "FingerLow" "-10"
	Option "FingerHigh" "5"
	Option "JumpyCursorThreshold" "280"
	Option "FingerPress" "200"
	Option "EdgeMotionMinZ" "10"
	Option "ResolutionDetect" "true"
# tweak the X-server pointer acceleration
        Option "AccelerationProfile" "2"
        Option "AdaptiveDeceleration" "8"
        Option "ConstantDeceleration" "16"
        Option "VelocityScale" "32"
        Option "AccelerationNumerator" "30"
        Option "AccelerationDenominator" "10"
        Option "AccelerationThreshold" "10"
        MatchIsTouchpad "on"
# This option is recommend on all Linux systems using evdev, but cannot be
# enabled by default. See the following link for details:
# [http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html](http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html)
      MatchDevicePath "/dev/input/event*"
EndSection

Section "InputClass"
        Identifier "touchpad ignore duplicates"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/mouse*"
        Option "Ignore" "on"
EndSection

# This option enables the bottom right corner to be a right button on
# non-synaptics clickpads.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Default clickpad buttons"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
#       To disable the bottom edge area so the buttons only work as buttons,
#       not for movement, set the AreaBottomEdge
#       Option "AreaBottomEdge" "82%"
EndSection

# This option disables software buttons on Apple touchpads.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Disable clickpad buttons on Apple touchpads"
        MatchProduct "Apple|bcm5974"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "0 0 0 0 0 0 0 0"
EndSection

---

### Post by rob53 on 2014-04-28
[COLOR=#404040][FONT=arial]I tried this and it made my cursor movement incredibly slow. A swipe of the trackpad would cover 20-30 pixels on my screen. I increased the maxspeed, minspeed and accelfactor variables but only managed to gain 60 or so pixels, so I started reducing the negative acceleration variables by half each time, and eventually ended up with a mouse cursor that basically drew a square when I was drawing a circle. After some more tweaking it had a few improvements, and I even tried the code listed in Ubuntu's documentation for 2,1 macbooks as well as the 10.04 distro, it still didn't help.

[/FONT][/COLOR]
[COLOR=#404040][FONT=arial][I also installed the patch here]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1034132").  It didn't make the cursor work right. I have to get productivity back on this machine so I tried Ubuntu 14.04 to see if they added compatibility with this trackpad. It doesn't work, so I'm going to have to go back to Snow Leopard. Apple cut support for snow leopard so I wanted to switch to Linux but I need the trackpad.[/FONT][/COLOR]

According to this person, it's not just the driver but Apple's integration of hardware with software:

[http://www.reddit.com/r/answers/comments/1sr3fd/why_does_mac_os_xs_trackpad_move_so_much_better/ce0moaw](http://www.reddit.com/r/answers/comments/1sr3fd/why_does_mac_os_xs_trackpad_move_so_much_better/ce0moaw)

---

### Post by sam.merriment on 2014-11-15
[https://github.com/sprc/appletouch](https://github.com/sprc/appletouch)

Install this then run the install script.

---

### Post by rsavage on 2014-11-24
> **gwjvan said:**
> Also, it seems when the kernel is updated from software updates, the appletouch driver is reset, and step 10 above needs to be done again to get the new driver. (It has done this a couple of times since I wrote the steps above)

[QUOTE=nortexoid]I see that settings are LOST when the kernel is upgraded. This makes maintaining a usable touchpad a big pain in the butt.[/QUOTE]

You could use DKMS to automate things like I did with some snd-aoa modules - [http://ubuntuforums.org/showthread.php?t=2209340&page=7&p=13173354#post13173354](http://ubuntuforums.org/showthread.php?t=2209340&page=7&p=13173354#post13173354)

---

