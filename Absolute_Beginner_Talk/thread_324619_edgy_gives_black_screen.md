---
title: "edgy gives black screen"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-12-24
hi all, 
i had to remove my ubuntu installation because i messed up with it alot, now i'm re-installing it but the thing is that after finishing the installing "in text mode" it doesn't boot! it gives the usplash screen and then goes blank!
any ideas?i used to do this before and as i remember i installed the older 5.10 version then upgraded to 6.10 but i dnt want to do that! any suggestions?
thanks

---

### Post by taurus on 2006-12-24
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
startx
```
(If you're not sure about an answer, just use the default...)

---

### Post by Mazen on 2006-12-24
perfect thanks i'm gonna try that ...get back to here in a while

---

### Post by Mazen on 2006-12-24
one more question not related but is it better to install on a ext3 or 2 partition?

---

### Post by spockrock on 2006-12-24
I say ext3 is better its just a journaled ext2 filesystem.

---

### Post by Mazen on 2006-12-24
ok i'm in the reconfiguration of my xserver-xorg and it's asking me for Video Card's bus identifier!!! how do i know that!? is the one written the default one?

---

### Post by spockrock on 2006-12-24
my best bet would be yes......

---

### Post by Mazen on 2006-12-24
hey spockrock what's Ubuntu Satanic Edition Developer??

---

### Post by Mazen on 2006-12-24
> **taurus said:**
> Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
startx
```
(If you're not sure about an answer, just use the default...)

i did the reconfiguration and it still doesn't work! gives the usplash and then the scren turns off!

---

### Post by spockrock on 2006-12-24
> **Mazen said:**
> hey spockrock what's Ubuntu Satanic Edition Developer??

ummm, as a joke, Ubuntu Satanic Edition was created, its mostly just theme work, however, I have been working on making a live disc, actually I am posting from the live disc, but yeah, I am a dev on Ubuntu Satanic Edition.

[http://parker1.co.uk/satanic/](http://parker1.co.uk/satanic/)

---

### Post by Mazen on 2006-12-24
cool good luck with that...now dev something for me lol!

---

### Post by spockrock on 2006-12-24
ok what are you system specs, lets see if you have hardware, that might be the cause of your woes.


Also what happens when you try to boot off the 6.10 live disc??

---

### Post by Mazen on 2006-12-24
well yeah i have an ATi x700 graphic card on my laptop
i tried booting from a live disk but no use gives a black screen too...i have 6.10 DVD i'm gonna try that now live but it'll do the same i'm pretty sure

---

### Post by spockrock on 2006-12-24
sorry, but what laptop do you have??  Also what about 6.06? does that do the same thing.

if you know the model, we can see if there is a reported bug, and if there is a fix, or workaround.

---

### Post by 3dimentia on 2006-12-24
> **Mazen said:**
> hi all, 
i had to remove my ubuntu installation because i messed up with it alot, now i'm re-installing it but the thing is that after finishing the installing "in text mode" it doesn't boot! it gives the usplash screen and then goes blank!
any ideas?i used to do this before and as i remember i installed the older 5.10 version then upgraded to 6.10 but i dnt want to do that! any suggestions?
thanks

You sound like you have an nvidia card ya?

at the blank screen, hold cntrl + alt and press F1
that'll take you to the command line.
cd /
cd etc/X11
sudo pico xorg.conf

this opens up the pico text editor, scroll down till you see a line that looks like this:
Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

this is the "device" section.  change the driver from what is most likely "nv" to be "vesa"

press CNTRL+o to write the file out, it'll ask you what to save the filename as, just hit enter.
then hit cntrl+x.  That exits.
you should be able to then hold alt+cntrl and press f7.  This will take you back to the screen that should be your graphical desktop.  Press cntrl+alt+backspace, and it'll reboot the X server (graphic server)  if it starts up, and graphics are there, awsome, you have a start to gettin your set up working again :)

Hope that all helped!

cheers

---

### Post by spockrock on 2006-12-24
also since you have installed it, and after usplash you get nothing but black screen, can you boot into single user mode or recovery mode (grub menu)??

---

### Post by Mazen on 2006-12-24
yep i can
and from there i reconfigured xserver-xorg but still does the same thing....live ddnt work either

---

### Post by Mazen on 2006-12-24
> **spockrock said:**
> sorry, but what laptop do you have??  Also what about 6.06? does that do the same thing.

if you know the model, we can see if there is a reported bug, and if there is a fix, or workaround.

it's a toshiba satellite ....i had this problem before but there is no "precise" and predefined way to fix it...it's always tial and error!!

---

### Post by spockrock on 2006-12-24
ok have you tried to install the ati drivers in single user mode?  this sounds like a gfx issue.

---

### Post by Mazen on 2006-12-24
how do i do that!

---

### Post by Mazen on 2006-12-24
if you have a quick solution or something i'd be glad if you post it and i will check it first thing in the morning! it's 5AM now! lol
10x for ur help

---

### Post by spockrock on 2006-12-24
ok btw I found a possible solution to your issue,

boot single user mode, install the ati-drivers, edit your xorg.conf and in the monitor section add

Option "MonitorLayout" "LVDS,CRT"

that might fix it.  The problem isn't that your screen is black but apparently turning off, you actually will get something after the usplash if you connect an external monitor to your secondary output.

---

### Post by Mazen on 2006-12-24
ok how do i install the drivers if im in single user...i have the bin file can that be done through it?..Ati fdriver bin file

---

### Post by spockrock on 2006-12-24
> **Mazen said:**
> if you have a quick solution or something i'd be glad if you post it and i will check it first thing in the morning! it's 5AM now! lol
10x for ur help

hahahha its 5am here, toronto and montreal are the same time zone.... lol.... yeah ok first boot into single user mode, you should be root user by default.  First thing is first, make sure you have the right repositories enabled.  so first we should backup your sources.list in case you make a huge mistake. so 

```
cp /etc/apt/sources.list /etc/apt/sources.list.bak
nano /etc/apt/sources.list
```

to enable all the ubuntu repositories, make the file look like this,
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main
```

btw side note if you want the plf repos as well here they are, just add these to the bottom of the file.

```
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free non-free
```

then
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

```

then we edit your xorg.conf, but first back up....

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
nano /etc/X11/xorg.conf
```

now first find the driver "ati" in the video card section, to driver "fglrx"

```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
``` 
add that to the end of the file and add this option in your gfx card section  

```
Option "MonitorLayout" "LVDS,CRT"
```

so it should look something like this, ONLY change what I told you to change if identifier or BusID is different then leave them as is.

```
Section "Device"
	Identifier	"x700 mobile"
	Driver		"frglx"
	BusID		"PCI:0:2:0"
        Option          "MonitorLayout" "LVDS,CRT"
EndSection
```

then do this,
```
sudo aticonfig --overlay-type=Xv
```

then sudo reboot and it should in theory work.

---

### Post by Mazen on 2006-12-24
ahhh!!! i see light!!
10x mate

---

### Post by spockrock on 2006-12-24
so it worked???

---

### Post by glantucan on 2006-12-30
Hi folks
I did install the frglx new driver following tutorial:[http://www.ubuntu-es.org/index.php?q=node/19975&page=3](http://www.ubuntu-es.org/index.php?q=node/19975&page=3)

Sorry it's in spanish but for linux speakers like you this should not be a problem. 3d acceleration an DRI are working.
 fgl_glxgears shows around 700 FPS (which I still think is slow but enough)
I use a fujitsu-siemens amilo 1437g with the same x700 ati card you are talking about and with a 1Gb of ram
The main problem though, is that when shuting down, rebooting or trying to change to console mode (Ctrl+Alt+F1) the computer completely hangs and I have to restart by brute force.
Any idea?

Thanks in advance
Glantucan

---

### Post by Mazen on 2006-12-30
Yeah it did!
i just have a question about LG3D if anyone knows about it?
i installed it and everything but it's not working how it should, again i have ATI i only found configs for nVidia and it's slow and stuff so any help?
thanks again guys

---

### Post by Mazen on 2006-12-30
Concerning the Ctrl+Alt+F1 and stuff like that i didn't get it fixed yet, i think it's an ATi issue still being worked on since ATi are known for their great cards but less greater drivers lol

---

### Post by glantucan on 2006-12-30
Ok, but any workaround or dirty trick there?
I don't like very much just to turn off the computer to shut it down :(

---

### Post by Mazen on 2006-12-30
What do you mean turning it off, u can always shut it down through the terminal or for "emergencies" go Ctrl+Alt+F1 then Ctrl+Alt+Del and it'll reboot.
I just didn't get what you mean...

---

### Post by glantucan on 2006-12-31
That's the problem, when I go Ctrl+Alt+F1 the computer hangs 
:) 
So I'm *umounting* everything but / before "shutting down". But I don't think my laptop is going to like it for long

---

