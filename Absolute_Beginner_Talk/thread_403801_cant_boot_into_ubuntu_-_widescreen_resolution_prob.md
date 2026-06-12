---
title: "cant boot into ubuntu - widescreen resolution problem?"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Einherjer1000 on 2007-04-07
Hello,

I'm semi new to Ubuntu and linux. I'm trying to install Ubuntu on my PC. So far I tried 6.8 and 7.04 and I get the same problem. I am able to boot into live CD, install Ubuntu, but when booting from the hard drive installation, my screen goes black after the loading bar screen completes. My screen goes dark and shows that its switching between analog and digital inputs, meaning that its not getting any signal.

I rememember that some time ago, I was able to install 6.8 and was able to boot into it, however I messed it up by trying to install ati drivers so I deleted the partitions and reinstalled it. I have this problem since then.

My video card:  Radeon 8500 DV with DVI output
Monitor: Samsung SyncMaster 941 BW with native resolution of 1440 x 900 connected using DVI input

Any help is greatly appreciated!

---

### Post by LaurelLynn on 2007-04-07
Dear Einherjer1000,

The first rule of changing your X configuration is make a copy of  /etc/X11/xorg.conf.  Everyone fails to do that once, and then the keep backup copies everywhere imaginable.

All PCs since the stone ages have video controlers compatible with the VESA  drivers in SVGA modes. So to get back to Gnome (where you can try again). I would copy that file somewhere safe then replace the Device, Monitor, and Screen setting with the following:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection


That is straight out of my xorg.conf.  It makes a good fallback, because it should work on any but the oldest of video cards.  Once your functional again you can search for another guide to installing better drivers.

Laurel Lynn

---

### Post by Einherjer1000 on 2007-04-07
Thank you for the information Lauren, but could you tell me how i can edit the file from recovery console, since I cant boot into gnome?

---

### Post by ajgreeny on 2007-04-07
sudo nano /etc/X11/xorg.conf

When you have made the changes hit Ctrl+X to exit and save.

---

### Post by LaurelLynn on 2007-04-07
If you aren´t comfortable without a graphical editor.

You could boot from the Live CD. From there you can run ¨sudo gedit¨ from a terminal to get root access to  any file you open: File->Open  (you may have to mount or remount the drive partition to get write access).

Laurel Lynn

---

### Post by dstew on 2007-04-07
I recently had a similar problem, but I just changed one thing in my /etc/X11/xorg.conf. I found the section where the video card was listed as a device, and changed the driver line from "ati" to "vesa". Worked fine after that.

---

### Post by Einherjer1000 on 2007-04-07
thank you very much to both of you! I am now able to boot into gnome!

:guitar:

---

### Post by APGunner on 2007-04-12
I am having sort of the same problem. I am trying to boot the livecd of a 64 bit version of ubuntu, it gets to the screen where i can select my options for booting it such as safe graphics mode and such, but when i hit safe graphics mode or the regular one they both give me the same thing. My monitor turns black and switchs back and forth between analog and digital. I have a 20 inch Samsung 206bw widescreen monitor. The 32 bit version of ubuntu boots just fine for me though which is weird because the 64 bit version doesn't. I want to get the 64 bit version install so I can get more out of my amd processor. If you need any more of my computer specs just tell me.

---

### Post by For the Birds on 2007-06-06
Ok, I'm having the same issue.  I'm very new at this....I just installed Ubuntu 7. 0 on my Dell Inspiron E1505. The installation goes fine but when the computer reboots from the hard drive I see nothing but a dark screen.  I tried using sudo dpkg-reconfigure xserver-xorg after login in to modify the configuration and after this when the computer booted I had a total dark screen.  No longer able to click shift-alt- F1. 
So now I reinstalled ubuntu and I'm about to try it again.  I read somewhere that changing the video card name from ati to Vesa might do the trick.  Anybody with suggestions please help

:(

---

