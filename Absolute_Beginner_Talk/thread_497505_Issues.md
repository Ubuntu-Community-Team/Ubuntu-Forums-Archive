---
title: "Issues"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by tnthomas17 on 2007-07-10
OK, I'm really not sure which forum to post this on, so I'll post it here.

I have just installed Feisty on my desktop PC, but it does not have a wired internet connection, and it's wireless card is an MSI PC54G.

It also won't let me enable the NVIDEA 3d 'restricted driver' for whatever reason.

I have no simple way of connecting the desktop box to the internet other than booting it to windows.

Thank you for your time

---

### Post by ikonia on 2007-07-10
hi,

what are the problems or errors you get when you try to install the nvidia restricted drivers ?

what make and model is your network card ?

What chipset does your MSI wirless card use ?

---

### Post by tnthomas17 on 2007-07-10
1) When I try to install the nvidia from the restricted device manager, I get a window confirming installation, but it does absoutely nothing. After a system reboot (which it recommended to activate the new video driver) it still told me the same thing when I checked to see if it was enabled. 'disabled'

2) It's an MSI pc54g, that's as best as I know for make and model;

3) But it's a broadcom chipset. drivers are ms68bm.inf and/or ms68bm.sys as referred by the ndiswrapper website.

but, ndiswrapper is not installed on the desktop.

---

### Post by Nekiruhs on 2007-07-10
Sometimes the restricted driver manager is weird. Lets do this manually.
```
sudo apt-get install nvidia-glx-new
```
then ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BACKUP
```
(Reverse this step if X fails to start)
```
gksudo gedit /etc/X11/xorg.conf
```
Now look for a section labeled Device
(This is mine)
```
Section "Device"
	Identifier	"nVidia Corporation C51G [GeForce 6100]"
	[COLOR="Red"]Driver		"nv"[/COLOR]
	Busid		"PCI:0:5:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection
```
Now,  see where it says "nv" change that to "nvidia"
It'll look like this:
```
Section "Device"
	Identifier	"nVidia Corporation C51G [GeForce 6100]"
	[COLOR="Red"]Driver		"nvidia"[/COLOR]
	Busid		"PCI:0:5:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection
```
Save and close Gedit
Restart X by pressing Ctrl + Alt +Backspace (This closes all apps, so save any open documents etc.)
You should be using the Nvidia proprietary drivers now.

---

### Post by tnthomas17 on 2007-07-10
The only issue of this is that I have no internet on the box in question.

is there any way to update the drivers without having access to the internet on the box in question? ((I.e. download them to a drive then install them that way?))

---

### Post by Nekiruhs on 2007-07-10
> **tnthomas17 said:**
> The only issue of this is that I have no internet on the box in question.

is there any way to update the drivers without having access to the internet on the box in question? ((I.e. download them to a drive then install them that way?))
You have the Live CD right? Boot your installed system. Pop in the Live CD, go to synaptic (System > Adminstration > Synaptic Package Manager) Go to edit and click add cdrom. Then run the commands I gave. [COLOR="Red"]IMPORTANT: If nvidia-glx-new DOES NOT install DO NOT touch the xorg.conf, STOP my instructions if nvidia-glx-new does not install.[/COLOR]

---

### Post by tnthomas17 on 2007-07-10
tried with the live cd, and this is what I get:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-new has no installation candidate

---

### Post by Nekiruhs on 2007-07-10
Try just installing nvidia-glx instead of nvidia-glx-new

---

### Post by tnthomas17 on 2007-07-10
same issue when I try to do sudo apt-get install nvidia-glx

it also gives me an error when i try to add cdrom saying unable to mount cdrom

---

### Post by tnthomas17 on 2007-07-10
I'm wondering if it would just be easier to drag my box up to someplace that has a wired connection and do the apt-gets there, though I'm still not certain of how to use ndiswrapper once I got it ready to use.

---

### Post by Nekiruhs on 2007-07-10
> **tnthomas17 said:**
> I'm wondering if it would just be easier to drag my box up to someplace that has a wired connection and do the apt-gets there, though I'm still not certain of how to use ndiswrapper once I got it ready to use.
It might just be easier. Linux can be a pain with no internet.

---

### Post by tnthomas17 on 2007-07-10
The hard part is finding somewhere I can actually plug a desktop into the internet. I have a wireless card on it, I just need ndiswrapper in order to be able to use it, I have the drivers, just no ndiswrapper

---

### Post by tnthomas17 on 2007-07-15
Oh the ultimate in Irony...

I used the same .deb package that someone had given me for my laptop's driver, and it made my new desktop work wirelessly as well... HOW COOL IS LINUX????

Thank you all for your help,
and God bless you!

Tim

---

