---
title: "help with my G3 ibook using mac os tiger"
date: 2010-03-06
forum: Apple Hardware Users
---

### Post by koyigo on 2010-03-06
I recently deleted the file Library under the following thread Macintosh HD/system/'Library' on my ibook after which there was a blackout and it went off. On trying to put it on, all I got is a grey screen.unfortunately, i lost its restore CD  wat can I do inorder to get my ibook working? is there a version of linux or ubuntu that i can install in it in place of the mac os? Please help.koyigo 
specifications:- ibook g3, 128MB, 10GB HDD

---

### Post by linuxopjemac on 2010-03-06
If you want an easy solution, go for Debian Lenny PPC. Take the net installer if you have a wired connection.

[http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-netinst.iso](http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-netinst.iso)

---

### Post by koyigo on 2010-03-08
when i put on my ibook, all i get is the gray screen. wat do i do? how can i run the image? can i run it from a flash drive?

---

### Post by linuxopjemac on 2010-03-08
CTRl-Alt-F1
you enter a tty
issue the following:
```
sudo passwd
```
create a root password here
then
```
su
nano /etc/X11/Xorg.conf
```
and then paste the following in the editor:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"false"
	Option		"SWcursor" 		"true"
	Option 		"ForcePCIMode" 		"true"
#	Option 		"XAANoOffscreenPixmaps"

EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 (AGP)"
	Monitor		"Standardbildschirm"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

Then CTRL-X and "y" to save
then go back to the installer 
CTRL-ALT-F7 (or some other key in that area)

---

### Post by linuxopjemac on 2010-03-08
if you cannot boot from CD go into open firmware:

start your mac with the on/off button
then press:
option+command+o+f

you then enter open firmware
then you do this

```
boot cd:,\\:tbxi
```

---

