---
title: "Use Beryl in Macbook"
date: 2007-05-10
forum: Apple Intel Users
---

### Post by curtisl.k on 2007-05-10
Hi, I'm using Macbook Core Duo with integrated display chipset. It's seems that the Beryl is successfully installed to my Ubuntu since I can open a Beryl-Manager. Even I press the shortcut key, the expected effect is not shown up. So do I use the Emerald-Manager to change the theme. Any idea or tutorial to teach me on these issues? Thanks.

Regards,
Curtis

---

### Post by curtisl.k on 2007-05-10
Dears, one more thing, I cannot enable the Desktop Effect too.

---

### Post by ronocdh on 2007-05-10
Have you installed the 915resolution package from the repos?

---

### Post by benanzo on 2007-05-10
just to see the extent of the problem, do this in a terminal:

```
glxinfo | grep direct
```

if you get this:
```
direct rendering: Yes
```
then it is a beryl problem.

If you get this:
```
direct rendering: No
```
then it is an xserver problem and we'll dig a little deeper.

I have the same machine as you and beryl works out of the box, so we'll see why it's not working for you.

---

### Post by curtisl.k on 2007-05-10
The result after I typed the command "glxinfo | grep direct" is XLib: extension "GLX" missing on the display: "0.0". Is there any missing package ??? Thanks.

Curtis

---

### Post by benanzo on 2007-05-11
be sure that you have 915resolution installed
```
sudo apt-get install 915resolution
```
if you just install it, reboot for the changes to take effect.

make sure you have these packages installed:
```
sudo apt-get install libgl1-mesa-dri libgl1-mesa-glx mesa-utils
```

make sure the Modules section in /etc/X11/xorg.conf looks like this:
```
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"v4l"
	Load	"vbe"
	Load    "i2c"
EndSection
```

make sure your Device section has:
```

Section "Device"
	Identifier	"Intel GMA950"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option  	"XAANoOffscreenPixmaps"
EndSection

```

NOTE:  don't change **Identifier** or **BusID** just leave yours as it is now.


make sure this is at the bottom:
```
Section "DRI"
	Mode 0666
EndSection
```

If you changed/added any of the above info to your system, then reboot and try the glxinfo command again.

if it says "Yes"

then Beryl should work.

---

### Post by curtisl.k on 2007-05-11
Even I've checked the xorg.conf file, the Load glx and Load dri sentences are here.

Here is my device section,
Section "Module"
   Load "i2c"
   Load "bitmap"
   Load "ddc"
   Load "drv"
   Load "extmod"
   Load "freetype"
   Load "glx"
   Load "int10"
   Load "vbe"
EndSection

Section "Device"
   Identifier "Generic Video Card"
   Driver "vesa"
   BusID "PCI:0:2:0"
EndSection

Thanks.

Curtis

---

### Post by benanzo on 2007-05-11
Ahhh....I see the problem right away.

Change "vesa" in your Devices section to "i810"

The vesa driver has no acceleration support whatsoever.

After you make the change restart the xserver or reboot.

---

### Post by curtisl.k on 2007-05-11
Oh, my Ubuntu's screen cannot be started up now.

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"v4l"
	Load	"vbe"
	Load    "i2c"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option  	"XAANoOffscreenPixmaps"
EndSection

Section "DRI"
	Mode 0666
EndSection

Thanks.

Curtis

---

### Post by benanzo on 2007-05-11
I'm sorry that happened.

to get your screen back do this at prompt:
```
sudo nano /etc/X11/xorg.conf
```
change i810 back to vesa
ctrl-o to save
ctrl-x to exit
then:
```
startx
```

We need to see what the error was that you got when you loaded the i810 driver

do this at a prompt:
```
cat /var/log/Xorg.0.log | grep EE
```

post the output here.

---

### Post by curtisl.k on 2007-05-11
I've just started a clean installation on the Ubuntu. I've found that there is an error "Wrong chipset detected. 915resolution only works with Intel 800/900 series graphic chipsets." Actually, my Macbook is running on Intel GMA950 and I think that it's a 900 series.

Regards,
Curtis

---

### Post by curtisl.k on 2007-05-11
after running "cat /var/log/Xorg.0.log | grep EE"
The result is:
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom


Thanks.

Regards,
Curtis

---

### Post by benanzo on 2007-05-11
That is bizarre.  I have the same machine as you with the Intel GMA950 graphics chip and Beryl/AIGLX has worked out of the box for me everytime.

It is especially bizarre that 915resolution doesn't recognize your chipset.

Just to be clear, run this in a terminal to see exactly what chip you have:

update your PCI bus IDs
```
sudo update-pciids
```
then
```
lspci | grep Display
```

it should return:

```
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

---

### Post by benanzo on 2007-05-11
Are you using Parallels?  if you are, this is the problem.  I noticed in your other post about transferring files between OS X and Ubuntu in Parallels.

Unfortunately you wont be able to enable 3D rendering via Beryl on Ubuntu if it is installed in an emulated environment (Parallels).  This is because Parallels creates "virtual" devices (ie graphics chips) that are very generic and appear to the guest OS , in this case Ubuntu, to be very low-end.  That is why when you first ran Ubuntu it installed the "vesa" driver for your "virtual" graphics chip.  The vesa driver is kind of like the mother-of-all-graphics-drivers because it will work with *anything*.  Without getting too technical, it's because it reads/writes from the framebuffer rather than utilizing the chip's hardware processing capabilities which is required if you want to do any kind of composite/3D effects.

If you really want to run Beryl, you'll need to install Ubuntu directly on the hardware.  It is a breeze to install and setup on the first-gen MacBooks.  Most-all the hard stuff has been figured out and we can offer you great guidance should you choose to do so.

Excellent info right here:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by curtisl.k on 2007-05-11
Oh, my Ubuntu is run on Macbook via Parallels! Then I have to able to install it to other machine as well. Ha!
Thanks for your help so much!


Regards,
Curtis

---

