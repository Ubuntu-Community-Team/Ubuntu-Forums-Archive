---
title: "screen resolution stuck at 800x600"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by cheetah_thompson on 2008-01-06
I'm new to Linux/Ubuntu as of yesterday. My screen resolution options are stuck at 800x600 or 640x480, so I've been trying to figure out how to fix this. My monitor is an Acer AL1916W and under Windows XP Home I have no problem using 1400x1050. My motherboard has an integrated graphics card, and Linux/Ubuntu sees this as a nVidia C51PV [GeForce 6150] as you can see from this paste from my /etc/X11/xorg.conf below. Do I need to modify this file to get the 1400x1050 resolution option to appear under System->Preferences->Screen Resolution? Is there a different driver I need (other than 'nv') and if so how would I get it?

Thanks in advance for any help.

-----------------------
/etc/X11/xorg.conf
-----------------------


Section "Device"
	Identifier	"nVidia Corporation C51PV [GeForce 6150]"
	Driver		"nv"
	BusID		"PCI:0:5:0"
EndSection
 
Section "Monitor"
	Identifier	"AL1916W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51PV [GeForce 6150]"
	Monitor		"AL1916W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x1440" "1440x900" "1400x1050" "1280x1280" "1280x1024" "1280x960" "1152x921" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by philinux on 2008-01-06
<snip>

edit the file to move the third resolution to second position.

---

### Post by texas8112 on 2008-01-06
i had this same problem this morning...but i too and very new to ubuntu..

i am not 100% sure if this is what happened to get it back working for me but this what i did

i tried to change the theme and it said i needed to 'enable' my video card driver to get the 2d and 3d enhancements etc......so i did then it worked after i rebooted.

---

### Post by sailor2001 on 2008-01-06
sudo dpkg-reconfigure -phich xserver-xorg

---

### Post by cheetah_thompson on 2008-01-07
Changed the order as suggested and rebooted the machine. No change unfortunately. Still only presented with two screen resolution options.

---

### Post by cheetah_thompson on 2008-01-07
Tried this and it gave me the option of changing my driver from 'nv' to 'nvidia'. I did try the latter (and set it also in xorg.conf) - but screen resolution options didn't change, and Ubuntu complained about it not using the correct driver. Set it back to nv.

---

### Post by denizoglu on 2008-05-22
The very same problem over here. The desktop effects works, however all I can get as resolution is 800x600.

---

### Post by manicman on 2008-05-22
According to your xorg.conf you don't have the proprietary Nvidia drivers installed try looking here
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installation_of_both_ATi_and_nVidia_Graphics_drivers]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installation_of_both_ATi_and_nVidia_Graphics_drivers")
on how to install them

---

