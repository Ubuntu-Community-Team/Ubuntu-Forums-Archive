---
title: "ATI Radeon 9600 Video Card FAILED"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by rbrittner on 2008-02-25
Ok so a while back an update came out for the graphics card, i updated and next time i rebooted the video card was unrecognizable.  Anyways, it booted in low graphics mode and i picked the wrong driver.....i posed a while back on here and someone told me to do the following. 

boot in recovery mode and type 'sudo dpkg-reconfigure xserver-xorg'
(without quotes)

anyways, I do that and auto detect pick my card and get the following

/var/lib/dpkg/info/xserver-sorg.postinst: 2037: cut: Input/output error

Any ideas on how to fix this?????

Thanks in advance
Ryan

---

### Post by JoshuaRL on 2008-02-25
Could you try again, maybe this time from the Recovery mode, and do:
```

dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by rbrittner on 2008-02-25
Oh and if I boot regularly it just displays tiny horizontal lines (same brown color as the boot screen)

---

### Post by rbrittner on 2008-02-25
exact same error :(

---

### Post by JoshuaRL on 2008-02-25
Okay, can you post the output of:
```

gedit /etc/X11/xorg.conf

```
That won't allow you to make any changes, so don't worry about hurting anything.

---

### Post by rbrittner on 2008-02-25
here's the exact error after i run the above

gedit: error while loading shared libraries: libgnomecanvas-2.so.0: cannot open shared object file: Input/output error

---

### Post by JoshuaRL on 2008-02-25
So are you able to get into Ubuntu in Low Graphics Mode?

---

### Post by rbrittner on 2008-02-25
I can not get into Ubuntu in low graphics mode.  I ran some code in a similar post which is below

nano /etc/X11/xorg.conf 

The driver is set to vesa so i'm not sure why it's not booting in low graphics mode

Anyways, do you have any more ideas?  Is there a way to replace that file with an original on the CD?

Thanks for the help so far!

---

### Post by JoshuaRL on 2008-02-25
> Thanks for the help so far!

Don't worry about it man, just make sure that once you get comfortable with Ubuntu you come back here and help others.  That's what the community is all about.  And any time you feel like I'm moving too fast or that you want to understand it a little better just let me know.

Okay, so you can't see the GUI at all, right?  If so, then that may be why gedit didn't work.  It needs xorg to be running to work.  So could you post the section of your xorg.conf that says "Device Video Card"?

Just use the same command you did above:
```

nano /etc/X11/xorg.conf

```

You see, Linux uses a lot of plain text configuration files to control how apps and processes work.  So the xorg.conf file is the configuration file for your Xorg, which interfaces with the video card and the base OS to give you your GUI.

---

### Post by macogw on 2008-02-25
I think vesa *is* low graphics mode.  Just change where it says "vesa" to say "ati" so you've got the open source ati drivers going, and it should work.  That card's in the compuer I'm using right now.

---

### Post by rbrittner on 2008-02-25
Well no worries about going to fast, i'm pretty good with computers just not linux yet :D and don't worry as soon as i get more fluent in linux i'll live on these forums, I switched about a month and a half ago and couldn't have done it without the help here.  So thanks

ok so i ran the nano command and came up with the following under device

Section "device"
identifier "failsafe device"
boardname "ati radeon (vesa)"
busid "pce:1:0:0"
driver "vesa"
screen 0
vendorname "ati"

---

### Post by macogw on 2008-02-25
change:
driver "vesa"
to:
driver "ati"

---

### Post by rbrittner on 2008-02-25
ok so i changed the driver to just ati and now it starts booting in low graphics mode but then continues to loop to a command line with logon and password then flashes to a window that is black and has the busy cursor

---

### Post by JoshuaRL on 2008-02-25
Did you change it in the Device section under Video Card?  Because the one you posted there was for bridge I believe.

The section you want should look like:
```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

```

Try putting in "ati" where it reads "vesa".

---

### Post by rbrittner on 2008-02-25
ok so i got rid of all the code except the 3 lines you suggested and now it seems a little more stable.  one problem, i installed firestarter and it won't get past that booting....is there a way to take that out of the boot sequence.....man this is getting pretty crazy!!!

---

### Post by JoshuaRL on 2008-02-25
Okay, now that you have a GUI can you post your whole xorg.conf please?  I'm a little scared of something.

---

### Post by rbrittner on 2008-02-25
LOL, you too!  well the gui didnt' go as planned, it stops mid boot, I get the nice graphics that show the status bar but then hangs, I did a ctrl alt del and it came up saying someitng about x serve error and to contact my system admin....LOL, time for a fresh wipe?  I'll post the config if you still want me to

---

### Post by JoshuaRL on 2008-02-25
If you could that would be great.  I'm still optimistic we can fix this without a new install.

---

### Post by rbrittner on 2008-02-25
ok so here's the config file (still no GUI)

Section "module"
load   "v41"
endsection

section "input device"
identifier "generic keyboard"
driver "kbd"
option "corekeyboard"
option "xkbrules"    "xorg"
option "xkbmode1"   "pc105"
option "xkblayout"    "us"
endsection

then mouse section which is not important (i think)

Section "device"
Identifier  "generic Video Card"
Busid   "PCI:1:0:0"
Driver "vesa"
endsection

Section "monitor"
identifier "Generic Monitor"
Horizsync 30-71
Vertrefresh 75
Gama 1.0
Endsection

Section "screen"
identifier "default screen"
device "failsafe device"
monitor "failsafe monitor"
defaultdepth 24
subsection "display"
depth 24
virtual 1400     1050
modes "800x600@85"    "800x600@60" ...whole bunch more
endsubsection
endsection

section "serverlayout"
identifier "default layout"
screen 0 "Default Screen" 0 0 
input device "generic keyboard"
inputdevice "configured mouse"
endsection

section "device" #
Identifier   "device1"
boardname "ati radeon (vesa)
busid "pci:1:0:0"
driver   "vesa"
screen 1
vendorname "ati"
endsection

Section "screen" #
identifier   "screen1"
device "device1"
defaultdepth 24
monitor 'monitor1"
endsection

Section "monitor" #
identifier "monitor1"
gamma 1.0
endsection
section "serverflags'
endsection

ok so that's it,

---

### Post by JoshuaRL on 2008-02-25
Section "device"
Identifier  "Generic Video Card"
Busid   "PCI:1:0:0"
Driver "**ati**"
endsection

section "device" #
Identifier   "device1"
boardname "ati radeon (vesa)"
busid "pci:1:0:0"
driver   "**ati**"
screen 1
vendorname "ati"
endsection

Okay, i put in bold the sections I changed.  See if you can change that and notice any difference.

---

### Post by rbrittner on 2008-02-25
well it got to the screen about the low graphics card, gives me the option to select or continue, when i hit continue it goes to a black screen, this time the cursor is a low graphic watch instead of the spinning disk......almost going to just say screw it and reinstall.....unless there are any more ideas, i'm off to bed but i'll check the post in the morning, thank you all for your help.  

Ryan

---

### Post by JoshuaRL on 2008-02-26
Alright, I have a couple more suggestions before you go that route.

If you can get a GUI, even the low graphic one, try downloading and running [Envy.](http://albertomilone.com/nvidia_scripts1.html)  It will try to install and configure the correct ATI or Nvidia driver.

If you can't, I would try this (again):
```

dpkg-reconfigure -plow xserver-xorg

```
But this time try to manually select the "ati" driver.  It's a long shot, but it may work.

---

### Post by mekura on 2008-02-26
> **rbrittner said:**
> Ok so a while back an update came out for the graphics card, i updated and next time i rebooted the video card was unrecognizable.

Which driver did you update? ATI's proprietary 'fglrx', or the open-source 'ati'?
From the command line, does
```
tail /var/log/gdm/:0.log
``` or ```
tail ~/.xsession-errors
``` return anything noteworthy?

I had a similar problem with my Radeon 9600 after updating to the most recent 'fglrx' driver (after which neither 'fglrx' or 'ati' loaded), The problem was related to my monitor*. If nothing else works, if you post your monitor model and default resolution I *may* be able to help.

* specifically, the driver was trying to display an unsupported resolution.

---

### Post by rbrittner on 2008-02-26
Thanks Guys for your help, luckily all my data was on another hard drive, so now i'm just going to wipe.  I did the suggestions above and all returned nothing note worthy.  the dpkg-reconfigure code didn't even work any more (I must have messed something up) and the tail /var/log/gdm/:0.log only returned one weird thing, it said it was using the xorg.config.failsafe instead of just the xorg.config (well at least I thought that was weird....who knows though)  anyways, thanks again, 

Ryan

---

