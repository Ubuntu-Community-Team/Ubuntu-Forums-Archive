---
title: "Screwed up Monitor Settings"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by neoguy2012 on 2007-11-23
Hi,

First, I'd like to apologize for making this stupid blunder.  Okay... I just bought a new 22" Acer X223W monitor for my Laptop and I was trying to set it up in Kubuntu (Feisty Fawn).  I set up both the primary and secondary monitors as generic screens (which worked just fine).  Then I tried to change the resolution and pressed CTRL-ALT-Backspace to restart X-windows.  Then, the Kubuntu Logo appeared and, after a few seconds... a blank screen... except for the blinking terminal _ cursor.  I tried going through recovery mode and running the kdm from there, but the screen just turned green and I wasn't able to do anything.  Is there a way to force it to a certain resolution through the command line (1024x768 is the native resolution of my laptop's monitor)?  I would prefer not to reinstall since I've been using this for months now and I accumulated a lot of important files.  If push comes to shove, I can just try to back up the files and reinstall....  Thanks in advance. <!-- insert strange smiley here -->

---

### Post by daimaru on 2007-11-23
in future always make a backup of your xorg.conf file before messing with the resolution or the file.

hit ctrl+alt+f1 -->gets u terminal. login and edit your xorg.conf manually.

you can either manually edit your xorg.conf to change it back to what it once was. there might still be a backup file there called something like xorg.conf-<date created>. rename that one to xorg.conf and try afterwards to start x by typing 

```
startx
```

or rewrite your whole xorg.conf file by 
```
sudo dpkg-reconfigure xserver-xorg
```

manual way:

```
sudo nano /etc/X11/xorg.conf
```
go to section "screen"

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Samsung SyncMaster 214T"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1600x1200@65"	"1600x1200@60"	"1400x1050@60"	"1280x960@75"	"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

edit your Modes line to reflect your setup. so if you don't use 1600x1200 delete it or change it to the resolution you want.

---

### Post by neoguy2012 on 2007-11-23
Thanks!  I'll try that right now.

---

