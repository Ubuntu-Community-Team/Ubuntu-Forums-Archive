---
title: "Display goes blank b4 ALT install finishes (ATI Graphics)"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by paradisebmk on 2007-11-02
Hi,


YET ANOTHER ATI GRAPHICS CARD ISSUE!!


I have two  ATI HD 2600 PRO graphic cards. In Vista 32-bit Ultimate I'm OK after installing ATI drivers. I'm a newbie to Linux.

Ubuntu was distro of choice after reading and comparing (several reasons but that's somewhat off topic). First I tried Gutsy regular install with  what seems to be the usual display problems.  Opted for ALT (text) install after reading threads. The TEXT install goes well untill the end when the screen goes blank **before the install completes**. I don't seem to be able to do anything even though the computer is still running. 

So after this frustration,  I tried to install PClinuxOS. After much trial and error (again frustration) I booted open CD, installed ATI proprietary driver for Linux, downloaded ATI Proprietary driver for Linux installer and ran it, THEN finally actually installed it on hard disk so driver was already there, configured driver (again much trial and error)s but this is done now and OK. 

I want to use Gutsy but need to get past the 'blank screen issue' so that I can get on to installing the ATI driver and get a shot at all the other related issues I've been reading about.


Ideas are welcome (while I still have hair left)?

Regards,

ParadiseBMK (aka "Rob")

---

### Post by daimaru on 2007-11-03
EDIT: its probably enough to just install the linux-restricted-modules and do the dpkg-reconfigure xserver-xorg, but im not sure since i dont use ATI

well you said install worked with the gutsy live cd right? so just install it using live cd then you at least can finish the installation. if after install you only get a black screen cause xserver wont start, hit alt+ctrl+f1 login with your user and pass.

install your restricted ati driver dont know the package name, but you could search for fglrx
```
sudo aptitude search fglrx
```

and make sure you have the following packages installed. 

```
sudo apt-get install linux-restricted-modules-generic restricted-manager
```
```
sudo apt-get install xserver-xgl
```
**method1:**
after that either edit your xorg.conf file
```
sudo nano /etc/X11/xorg.conf
```
and change the driver under section device from "ati" to "fglrx"
```
Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8800 GTS]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection
```
the part where it says nvidia for me should read fglrx for you

**method2:** 
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by paradisebmk on 2007-11-04
Thanks for your detailed reply, daimaru. I really appreciate your time and effort to help me.I completed the install but as you said I get not a blank screen but a garbled one because of the resolution problems caused but the lack of the ATI driver.alt+ctrl+f1 work like magic....entered my userid/password and was in.I had two issues (for which I'll get more delail further down)1. I could not connect to [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com)
2. The label on the install CD differef from what it is looking for when it prompts me to insert it.

Is there a way to boot using VESA (or something  else--I just saw ESA somewhere) so that I can get the graphics up, correct the connection error, and install the proper drivers. I really am a newbie and don't know where to  start correcting the connections using command line. 

Thanks again for you time and assistance. Here are the details:

issued: sudo aptitude search fglrx

p   fglrx-control                 - control panel for the ATI graphics acceler
v   fglrx-driver                  - 
v   fglrx-driver-dev              -
p   fglrx-kernel-source           - ATI binary kernal module source
p   xorg-driver-fglrx             - Video driver for ATI graphics accelerators
p   xorg-driver-fglrx-dev         - Video driver for ATI graphics accelerators


 issued: sudo apt-get install fglrx-driver

Reading package list... Done
Note, selecting xorg-driver-fglrx instead of fglrx-driver
The following extra packages will be installed:
   gcc-3.3-base libstdc++5 xorg-driver-fglrx
The following NEW packages will be installed:
   gcc-3.3-base libstdc++5 xorg-driver-fglrx
0 upgraded, 3 newly6 installed, 0 to remove and 16 not upgraded
Need to get 8558kb/9005k of archives
After unpacking 24.1MB of additional storage will be used.
Do you want to continue [Y/n]?    answered: y
WARING: the following packages can not be authenticated!
   xorg-driver-fglrx
Install these packages without verification [y/N]?    answered: y

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted xorg-driver-fglrx 7.1.0-8.37.6+2.6.22.4-14.9
   Could not resolve 'us.archive.ubuntu.com'
Failed to fetch some archives, maybe run apt-get update or try with --fix-missing?

xserver-xgl  is pretty much the same except it asked to insertr the install CD but when I do the labels don't match and I get in a loop of "Insert ... then press ENTER"

---

