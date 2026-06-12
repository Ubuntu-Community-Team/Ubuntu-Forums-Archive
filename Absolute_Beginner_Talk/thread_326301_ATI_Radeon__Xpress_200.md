---
title: "ATI Radeon  Xpress 200"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by ZeldaFreak on 2006-12-27
hi, i am a completely new user to Linux. i have a Compaq presario with a ATI radeon xpress 200 graphics card and a AMD64 athlon processor.
ubuntu boots fine but i have some problems with my graphics card. i have managed to obtain a driver from the ATI website which doesn't seem to do anything. is there anything else i can do to make it work, to let screensavers and beryl etc to work. 
please use very simple terms as i am very new to linux and require some help.
thanks in advance.

---

### Post by cilynx on 2006-12-27
Quick answer is it ain't easy right now...

If this works for you, you're golden.  If not, it's a lot of work.

[http://ubuntuforums.org/showthread.php?t=318889](http://ubuntuforums.org/showthread.php?t=318889)

---

### Post by michaeljustman on 2006-12-27
Great news for you! I've just gotten this working on my HP Pavilion zv6000, which is the HP counterpart to your  computer.

It is possible. Fortunately, the drivers in the repository ( 8.24.8 ) work with the 200 and 200M, you shouldn't have to compile anything. If you're new to linux this is the best one to use for now because you don't have to compile the drivers or the kernel module.
[B]
EDIT:On the suggestion of cilynx, I tried the formentioned tutorial. It actually is quicker and easier than mine and you can use Sideport alone.[/B]

If you want the newest drivers, follow this tutorial:
[http://ubuntuforums.org/showthread.php?t=318889]("http://ubuntuforums.org/showthread.php?t=318889")

Here's how I did it.

[LIST]
[*]Go to your BIOS and enable UMA memory for your graphics card and set it to 128MB. (Unfortunately, Sideport and Sideport + UMA  don't work with the version of the drivers in the repository... older and newer drivers that might support these, don't work well with our card or might be unstable.)

[*]fglrx v8.24.8 in the repositories works well with the 200 and 200M. Go to synaptic and make sure they and linux-restricted-modules for your kernel are installed or open a terminal and type:

```
sudo apt-get install xorg-driver-fglrx fglrx-control linux-restricted-modules-generic
```

[*]Backup your xorg.conf so that *when* this fails the first couple times you can restore it from the recovery console:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

If you need to restore it boot into the recovery mode (from the GRUB menu) and type:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

[*]Add these lines to the end of your /etc/X11/xorg.conf:

```

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

```

You can open xorg.conf to edit by using this command in the terminal:
```
sudo gedit /etc/X11/xorg.conf
```

(replace gedit with mousepad if your are a Kubuntu or kde user.)

Also, change where it says:
```
Driver    "ati"
```

And replace "ati" with "fglrx".

Add these lines before "EndSection":

```

        Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
	Option "UseInternalAGPGART" "no"

```

Mine looks like this:
```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
	Option "UseInternalAGPGART" "no"
EndSection

```

[*]Back up your /etc/modules:
```
sudo cp /etc/modules /etc/modules.bak
```

[*]Add these lines to the end of your /etc/modules (these are the kernel modules loaded at boot... fglrx is already a part of the linux-restricted-modules and should already be installed):
```

agpgart
fglrx
dri

```

Open /etc/modules with this command in a terminal:
```
sudo gedit /etc/modules
```

(Remember replace gedit with your text editor of choice, if you use another version of Ubuntu)

Mine looks like this:

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
fuse
agpgart
fglrx
dri

```

[*]Next thing to do is reset your computer. Quickest way is to type in a terminal:
```
sudo shutdown -r now
```

[*]Verify that it works when you boot by opening a terminal and typing:
```

fglrxinfo

```


If it says something similar, go to the next step:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

Also check if direct rendering is enabled (this is very important, if not enabled your drivers aren't working). Type in terminal:
```
glxinfo | grep direct
```

If it says:
```
Direct rendering: Yes
```

You are good to go.

[*]If you get a black screen when you boot, make sure you have your BIOS set to use UMA *only*. Anything else won't boot right.

To restore your previous configuration, boot into the recovery console on the GRUB menu and type:

```

cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
cp /etc/modules.bak /etc/modules

```

Reset your computer with:
```

shutdown -r now

```

If this doesn't work for you. Pray and try again. Double check that you followed these directions or follow a different tutorial.

Good luck.
[/LIST]

---

### Post by ZeldaFreak on 2006-12-28
thank you very very very much :D graphics sorted.
apart from a small problem with beryl, i get this when i start up beryl:

XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension


what do i do?

---

### Post by michaeljustman on 2006-12-28
Not sure what that means, but I used this tutorial to install Beryl with use with XGL.

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL")

---

### Post by ZeldaFreak on 2006-12-30
thats the guide i been using.. but it still doesn't work :-?

---

### Post by cilynx on 2006-12-30
With this card, you have to use xserver-xgl as opposed to xserver-xorg.  The "soft" xgl in xorg has not been implemented by ATI in the binary drivers.  Unfortunately, in my experience, xserver-xgl is dog slow on this card and neither beryl nor compiz works anyway.  Both crash out for no good reason.  Do be sure to share if you get it working.

---

