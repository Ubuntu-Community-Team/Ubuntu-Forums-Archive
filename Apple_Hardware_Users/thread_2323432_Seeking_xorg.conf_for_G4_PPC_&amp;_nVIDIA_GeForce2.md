---
title: "Seeking xorg.conf for G4 PPC &amp; nVIDIA GeForce2 MX"
date: 2016-05-05
forum: Apple Hardware Users
---

### Post by lukon on 2016-05-05
Can someone write an xorg.conf file for my nVIDIA GeForce2 MX video card?

Here is my computer:

Apple Power PC G4 Quicksilver 867-M8493

[http://everymac.com/systems/apple/powermac_g4/specs/powermac_g4_867_qs.html](http://everymac.com/systems/apple/powermac_g4/specs/powermac_g4_867_qs.html)

Well, the box says that. But the OSX profiler utility says:

Machine Name: Power Mac G4
Machine Model: PowerMac3,5
CPU Type: PowerPC G4 (2.0)
Number Of CPU's: 1
CPU Speed: 733 MHz

So I don't know if it's 867 or 733.



The monitor is an HP vs19 recommending 1280 x 1024 @ 60 Hz

[http://support.hp.com/us-en/document/c00603942](http://support.hp.com/us-en/document/c00603942)



I have installed UbuntuMate Lubuntu 14.04.4 using the alternate install CD from this web page: [http://cdimage.ubuntu.com/lubuntu/re...14.04/release/](http://cdimage.ubuntu.com/lubuntu/re...14.04/release/)

Normally boots to a blank screen. But I can boot to a prompt using the &#8220;Linux text&#8221; command at yaboot.


So now I'd like to get the video to work right.

---

### Post by mörgæs on 2016-05-06
Maybe this works, I have not tried myself though:
[http://ubuntuforums.org/showthread.php?t=2130640&page=11&p=13219687&viewfull=1#post13219687](http://ubuntuforums.org/showthread.php?t=2130640&page=11&p=13219687&viewfull=1#post13219687)

---

### Post by lukon on 2016-05-10
> **mörgæs said:**
> Maybe this works, I have not tried myself though:
[http://ubuntuforums.org/showthread.php?t=2130640&page=11&p=13219687&viewfull=1#post13219687](http://ubuntuforums.org/showthread.php?t=2130640&page=11&p=13219687&viewfull=1#post13219687)


Thanks for your help, mörgæs

So I checked out the link you provided and assumed you meant that I should try the following:

> Using sudo

*** 1 ***
Create /etc/X11/xorg.conf.d/

*** 2 ***
create new file /etc/X11/xorg.conf.d/20-nouveau.conf
with the following text:

Section "Device"
Identifier "NvidiaGraphics"
Driver "nouveau"
Option "NoAccel" "1"
EndSection

Save this file, logoff, logon, and was happily astonished

Unfortunately, this did not work for me.

So I then tried the following replacement 20-nouveau.conf file (in the same directory), as recommended by the nouveau project website:

```
Section "Device"
    Identifier "n"
    Driver "nouveau"
EndSection
```

This improved the situation a bit. With this file, X would apparently start in a limited way, with a dark screen and a dash cursor flashing in the upper left corner. This is better than simply ceasing any signal at all to the monitor.

So then I tried a bigger 20-nouveau.conf file with settings for the monitor added. I found someone else's xorg.conf file that used the same monitor (the bottom post on this forum page: [http://forums.fedoraforum.org/showthread.php?t=110641](http://forums.fedoraforum.org/showthread.php?t=110641)) and took an educated guess as to how to adapt it for my set up. This is the result:

```
Section "Monitor"

### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
### Comment all HorizSync and VertSync values to use DDC:
	Identifier "Monitor0"
	VendorName "Monitor Vendor"
	ModelName "HP vs19"
	DisplaySize 380 300
	### Comment all HorizSync and VertSync values to use DDC:
	HorizSync 30.0 - 83.0
	VertRefresh 50.0 - 76.0
	ModeLine "1280x1024_60.00" 108.9 1280 1360 1496 1712 1024 1025 1028 1060 -hsync +vsync
	Option "dpms"
	# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
EndSection

Section "Device"
	Identifier "n"
	Driver "nouveau"
	VendorName "Videocard vendor"
	BoardName "nVidia Corporation [GeForce2 MX/MX 400]"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "n"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
	Viewport 0 0
	Depth 16
	Modes "800x600" "640x480"
	EndSubSection
	SubSection "Display"
	Viewport 0 0
	Depth 24
	Modes "1280x1024_60.00"
	EndSubSection
EndSection
```

This produced no improvement.

I have not yet tried anything else, other than updating the packages (sudo apt-get update/upgrade). I suspect that I might be close to a solution with a little more help.

---

### Post by gsahli on 2016-05-10
I've never got any version of linux/PPC with the nouveau driver to work. I got debian 6.0.10 to work because it has the older nv driver.
On the other hand, recently changed to a Radeon 9600XT card and got Debian Jessie 8.4 working. Still took some yaboot and xorg.conf experimentation.
(I have a G4 MDD 867 with couple of upgrades)

---

