---
title: "X server crash"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by hkq35 on 2006-11-29
My laptop was working OK ( trying to fix VLC) and I ran this script from [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
I ran
-- 
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

--
My problem is I have a normal Intel graphics card.
X server crashed... 
ran recovery mode
tried the commands found here 
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

It ran OK, but didn't get my x gui back

Looking for a simple way to uninstall these ATI/NVIDIA drivers and resort back to my previous xorg intel config???

---

### Post by rlozano on 2006-11-29
> **hkq35 said:**
> My laptop was working OK ( trying to fix VLC) and I ran this script from [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
I ran
-- 
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

--
My problem is I have a normal Intel graphics card.
X server crashed... 
ran recovery mode
tried the commands found here 
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

It ran OK, but didn't get my x gui back

Looking for a simple way to uninstall these ATI/NVIDIA drivers and resort back to my previous xorg intel config???

on the first place, you should have not installed any ATI or NVIDIA to your machine knowing that you have an Intel graphics. that's a big no.

try going to your /etc/X11/ directory and look for the oldest version of your xorg.conf, wherein it's using your interl graphics.

also, before doing that, remove that xorg-driver-fglrx. (sudo aptitude remove xorg-driver-fglrx && sudo aptitude update)

see if that will help.

---

### Post by greybirds on 2006-11-29
Have you tried running

```
sudo dpkg-reconfigure xserver-xorg
``` from the command line?

It will ask you a series of questions, one of which is what graphics driver you want to use. Intel graphics drivers are the ones starting with "i" with a number afterwards (i740, i810, etc.). If you know the name of your graphics chipset (or your computer's manufacturer can tell you), you're set. Otherwise you might have to try running it a couple times, selecting a different driver each time, but you'll get it eventually.

That *should* get your X setup back. You'll need to either reboot afterwards for it to take effect or, if you're using Ubuntu, you can type

```
sudo /etc/init.d/gdm start
```

instead of rebooting to get your desktop back.

---

### Post by hkq35 on 2006-11-29
rlozano
Yes ,hindsight,
Thanks for your suggestion
strangely there was no X11 folder in /etc/
I ran ( sudo aptitude remove xorg-driver-fglrx && sudo aptitude update)
it worked , but didn't fix it. The blue screen was still there after I rebooted

greybirds
Thank you also. I tried your suggestion too
Not much luck either I am afraid. Again it seemed to work , and after going through all the screens, the screen now booting gnome x server            [ok]
flashed a few times
then went back to a command propmt !!
incidently it's a i810 chipset

Getting close to giving up I think!

---

### Post by rlozano on 2006-11-29
it's just a xorg.conf problem. it was not properly configured. and i just wonder why you don't have a /etc/X11 directory.

if only you can post your xorg.conf content here, we shall be able to help you more. i will post here the i810 xorg.conf of my other machine. the info there might be able to help you.

---

### Post by rlozano on 2006-11-29
here's the section of my xorg.conf that you maybe interested of, for some information.

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
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


hope this helps.

---

