---
title: "Compiz problems"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by keithpaw on 2008-03-20
Hi  all
I have just installed Ubuntu 7.10 on my system for the first time and lovin it
I have installed compiz onto the system (no probs) but it did not have seemed to installed properly so i uninstalled

sudo aptitude -y remove compiz-core desktop-effects 
sudo aptitude -y remove compiz compiz-gnome 
sudo aptitude -y remove compizconfig-settings-manager 
sudo aptitude -y remove compiz-fusion-plugins-extra
sudo aptitude -y remove compiz-fusion-plugins-unofficial 
sudo aptitude -y remove libcompizconfig-backend-gconf

and tried again
and the same prpoblem has happend 
it will not let me click on custom or preferances in the appearance preferance but  the tag is there
i have changed the setting in the restricted device manager (restricted drivers) it tells me to reboot but it still the same
any ideas would be great (another noob)
 66oo gt pci ex
thanks

---

### Post by celticbhoy on 2008-03-20
Probably to do with your graphics driver & not compiz.

Please list system spec.

---

### Post by billgoldberg on 2008-03-20
> **keithpaw said:**
> Hi  all
I have just installed Ubuntu 7.10 on my system for the first time and lovin it
I have installed compiz onto the system (no probs) but it did not have seemed to installed properly so i uninstalled

sudo aptitude -y remove compiz-core desktop-effects 
sudo aptitude -y remove compiz compiz-gnome 
sudo aptitude -y remove compizconfig-settings-manager 
sudo aptitude -y remove compiz-fusion-plugins-extra
sudo aptitude -y remove compiz-fusion-plugins-unofficial 
sudo aptitude -y remove libcompizconfig-backend-gconf

and tried again
and the same prpoblem has happend 
it will not let me click on custom or preferances in the appearance preferance but  the tag is there
i have changed the setting in the restricted device manager (restricted drivers) it tells me to reboot but it still the same
any ideas would be great (another noob)
 66oo gt pci ex
thanks

Compiz was installed by default in gutsy, so you didn't need to install it.

You only need to install the compizconfig-settings-manager.

The problem (as stated before) lays with the graphics cards drivers.

Go to "system -> administration -> restricted drivers management" and enable your card there.

If it isn't listed, install it using[ envy]("http://www.albertomilone.com/nvidia_scripts1.html").

With my graphics card install, when I tried to enable the effects it gave a a "no composite supported" or something, so I have to modify xorg.conf (change composite from 0 to 1).

---

### Post by keithpaw on 2008-03-20
I'm using a 6600GT pci express graphics card and it has worked before on compiz  (a couple of days ago) but like all noobs i did something wrong and i reinstalled Ubuntu
and when installing compiz this time the problems have happend
regards
Keith

---

### Post by keithpaw on 2008-03-20
I have tried to install card drivers with ENVY but again it will not let me tick the box for the nvidia drivers

---

### Post by billgoldberg on 2008-03-20
> **keithpaw said:**
> I'm using a 6600GT pci express graphics card and it has worked before on compiz  (a couple of days ago) but like all noobs i did something wrong and i reinstalled Ubuntu
and when installing compiz this time the problems have happend
regards
Keith

You need to give more details:

Have you enabled your graphics card in 'restricted drivers management' or install them using envy?

If you haven't compiz fusion won't work.

So you removed compiz and reinstalled it, are you sure you installed it right?

Try starting compiz in the terminal (just type compiz): what errors does it give (copy past them here)?

---

### Post by keithpaw on 2008-03-20
here is the information from the terminal

keith@keith-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0140 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by billgoldberg on 2008-03-20
> **keithpaw said:**
> here is the information from the terminal

keith@keith-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0140 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

It seems to see you nvidea card, but not xgl:

```
sudo apt-get install xserver-xgl
```

After that log out and log back in.

---

### Post by keithpaw on 2008-03-20
loged back in and still still seems to be the same
I'm a a loss any more ideas please

---

### Post by billgoldberg on 2008-03-20
> **keithpaw said:**
> loged back in and still still seems to be the same
I'm a a loss any more ideas please

Run it in a terminal again and give the outcome

---

### Post by billgoldberg on 2008-03-20
Or take a look [here]("http://ubuntuforums.org/showthread.php?t=222034").

Sorry, that link extremely outdated and won't work.

---

### Post by keithpaw on 2008-03-20
ok here it is
keith@keith-desktop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by billgoldberg on 2008-03-20
I only have experiences with ati cards.

Post you xorg.conf file

"gksudo gedit /etc/X11/xorg.conf"

Some other users might be able to help you better.

Also try logging out and in again after you installed the xserver-xgl

---

### Post by keithpaw on 2008-03-20
ok heres the xorg file
nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Apr 16 20:37:13 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"

---

### Post by keithpaw on 2008-03-20
thanks for your help billgoldberg i will get there in the end i'll more than likely just reinstall
ubuntu

---

### Post by billgoldberg on 2008-03-20
There should be more in that file than what you copy/pasted

---

### Post by billgoldberg on 2008-03-20
Iit only takes about 20min to reinstall so it might be faster to do so.

Just remember that you only need to install the compizconfig package from synaptic, nothing else to make compiz run (the rest is installed by default).

---

