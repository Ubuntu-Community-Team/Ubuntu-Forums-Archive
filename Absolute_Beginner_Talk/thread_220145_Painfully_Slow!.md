---
title: "Painfully Slow!"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by rene100 on 2006-07-21
I'm new to Ubuntu, and haven't loaded a linux distro in several years.  I'm running a 2ghz pentium 4 mobile laptop with 1GB of ram, and Ubuntu is painfully slow!!!  I installed Dapper today and every program i load takes like 10 seconds before I get a response...

I tested for DMA and it is active, as well as 3d acceleration with my radeon 9000 graphics card.  I'm currently running thre pelink "sudo /etc/cron.daily/prelink" command which i read somewhere would speed things up (this is after installing the prelink package obviously) and so far it's been like 15 minutes and the command prompt hasn't indicated that the prelink is finished

I did updates and everything, but it still is rediculously slow.  Is it normal for it to take 10 seconds or longer to load and program?  

My boot seems pretty ok though 

PS I'm on an inspiron 8500 dell laptop.  PLEASE let me know if you have any suggestions as to what the problem might be

---

### Post by fatsheep on 2006-07-21
No it's definately not ok that it takes 10 seconds to load a program.  For me everything is super speedy compared to windows, not sure what's wrong with your setup.  Could you please post more detailed system specs?  Also if you have an overclock, I'd suggest removing that.

-sheep

---

### Post by rene100 on 2006-07-21
I'm running a full install of ubuntu 6.06 
on a laptop Dell Inspiron 8500
CPU is a 2GHZ mobile pentium 4M
1GB of RAM
650 MB swap I believe
Grapihcs card = Mobile Radeon 9000

uhhhh I can't think of anything else that may effect it other than the fact that I have 3 OSs on the computer, windows XP, OSX86 and Ubuntu 6.06

The prelink is completed and It still doesn't appear to be going much faster.  I still haven't switched back to IPv4 because I don't think that is the problem (since it's not just my internet that is slow)

I also switched the value of swappiness from 60 to 10

Still slowwwwwwwwwwwwwww :( :(

---

### Post by madmetal on 2006-07-21
is DMA on?
sudo hdparm /dev/hdc  and see about dma

---

### Post by Lord Illidan on 2006-07-21
Quick guess.

Run top in a terminal. Is gam_server mentioned anywhere?

---

### Post by rene100 on 2006-07-21
Yes DMA is on, so is prelink, 3d graphics acceleration too


output:

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

---

### Post by ThrobbingBrain66 on 2006-07-21
Switching to the 686 kernel from the 386 kernel could also give you a speed increase, if you haven't done so already.

---

### Post by Brunellus on 2006-07-21
I'm going to suspect something funny is up with your graphics drivers.  Was it slow before you installed fglrx?

---

### Post by rene100 on 2006-07-21
is it difficult to upgrade to 686?  That kernel doesn't come pre built into Dapper?

glxinfo reported that I had 3d acceleration on, but I don't know about this fglrx.  Is that a graphics driver?  Should I install it? is there instructions somewhere on that :)

---

### Post by rene100 on 2006-07-21
i'm installing the 686 kernerl atm :)

---

### Post by rene100 on 2006-07-21
OMG way better with the 686.  Still not flying in comparison to windows though, but waaaaaaay better.. Night and day :) thank you btw. 

Now i'll try the graphics pack that was recommended

---

### Post by Lord Illidan on 2006-07-21
Also, can you run top in a terminal, and post the results here?

---

### Post by rene100 on 2006-07-21
I installed the fglrx graphics pack that was recommended. and now glxinfo reports that there is no direct rendering (though with the 686 kernel the gui runs much better then before)  is there something i should do to activate it?

Here is a top output

top - 12:51:55 up 2 min,  2 users,  load average: 1.40, 0.74, 0.29
Tasks:  85 total,   2 running,  83 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.9% us,  1.0% sy,  0.0% ni, 83.8% id,  0.0% wa,  0.3% hi,  0.0% si
Mem:   1034400k total,   295060k used,   739340k free,     5852k buffers
Swap:   618460k total,        0k used,   618460k free,   165916k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5168 rene      16   0 32836  13m 8408 R  8.3  1.3   0:01.54 gnome-terminal
 4549 root      15   0 69600  20m 7328 S  6.6  2.0   0:06.59 Xorg
 5076 rene      15   0 27420 8884 7004 S  0.3  0.9   0:00.38 gnome-settings-
 5223 rene      16   0  2204 1040  828 R  0.3  0.1   0:00.03 top
    1 root      16   0  1568  500  432 S  0.0  0.0   0:01.26 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0
   10 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   11 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid-work-0
  144 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  145 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  147 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
rene@rene-laptop:~$

---

### Post by Lord Illidan on 2006-07-21
See if 3D accel works.

Either get a 3D game from the repos and play it (planet penguin racer is a good one), or else run glxgears -printfps in a terminal.

Also, can you give us your /etc/X11/xorg.conf file?

---

### Post by rene100 on 2006-07-21
the gears move fast for about 1 second, but then they practically stop moving

862 frames in 5.5 seconds = 156.865 FPS
398 frames in 8.0 seconds = 49.594 FPS
132 frames in 12.5 seconds = 10.602 FPS
133 frames in 5.6 seconds = 23.756 FPS
265 frames in 11.0 seconds = 24.153 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

---

### Post by Lord Illidan on 2006-07-21
> **rene100 said:**
> the gears move fast for about 1 second, but then they practically stop moving

862 frames in 5.5 seconds = 156.865 FPS
398 frames in 8.0 seconds = 49.594 FPS
132 frames in 12.5 seconds = 10.602 FPS
133 frames in 5.6 seconds = 23.756 FPS
265 frames in 11.0 seconds = 24.153 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

Right so 3D accel is not working correctly. Now can you paste your xorg.conf file here, please?

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by rene100 on 2006-07-21
here's the xorg.conf starting after the comments




Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Stan83 on 2006-07-21
With me the 686 kernel was actually slower than the default 386 :) (I've read in this Forum that it is due to some bug)

Run something that will tell you how much memory are you using, maybe you have a problem with something leaking memory, so nothing is left for you ;)
(I had it with Kubuntu, the KDE has a problem with default GTK style, the problem is also some ware in the forum, together with the fix for it)

---

### Post by Lord Illidan on 2006-07-21
I found this site which may help you continue.. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by rene100 on 2006-07-21
Thank you, I really appreciate all the help.

---

### Post by Stan83 on 2006-07-21
You could also use the Easyubuntu to install it...
I don't know how well it works though :)

---

