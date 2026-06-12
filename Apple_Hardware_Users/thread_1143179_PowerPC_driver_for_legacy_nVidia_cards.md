---
title: "PowerPC driver for legacy nVidia cards"
date: 2009-04-29
forum: Apple Hardware Users
---

### Post by djxfade on 2009-04-29
have an iMac G4
This machine have:
PowerPC 7441 CPU with Vector Unit (G4), 64K L1 Cache, 256K L2/L3 Cache.
1024 MB RAM (133 MHz),
200 GB IDE Harddrive,
nVidia GeForce 2MX/400 with 32 MB VRAM.

I hav just set it up with Ubuntu 9.04 "Jaunty Jackalope".
Everything runs pretty smooth(far greater than my expectations that is, I would compare ith with running Ubuntu on a P4).

My only issue is that Compiz Fusion (desktop effects) won't be actiavated.
This is of course baceause nVidia is too lazy to compile their proprietary binary-only driver for anything other than the o-migthy x86/x64.
Therefore I am locked to running a simple, standard framebuffer driver, which of course dont provide either 2D or 3D acceleration. (I get about 25 FPS running glxgears with framebuffer driver).

Is it anyone who might know if there exist an open driver for this card, which provide accelerated 3D, or at least accelerated 2D? Because now the GUI is far away from running as smooth as I am used to.

I tried to install the free driver, nouveau. But I got some weird error messages (is seems it just froze while compiling the kernel module). I tried to install it both through apt-get, and synaptics. And anyways, this "nouveau" driver does not yet as of current date officially support 3D.. 

Therefore the nouveau team wont provide any documentations on how to actiave the experimental 3D support in the driver.

I really would like to still be able to run Ubuntu on my dated iMac, as Mac OS X just wont do it for me. But as long as the GUI is so slow as it is right now, it is not pleasing. Far away from the Ubuntu experience I am used to, and believe me, I have runned Ubuntu on a lot of different setups, mostly x86/x64 though.

I think it also might be possible to run a compositing X session witch is CPU accelerated rather than GPU accelerated, but I am really concerned this would impact hard on the CPU, if not just strangle the CPU completely. (remember this is in fact a single core, 32-bit processor from 2001).

And, a little bit off topic. I have problems activating Desktop Effects on an iMac G3 with an ATI Rage 128 card, even though I know the free ATI driver support this card with 3D accelerations, any suggestions here? 
If there is anyone who could help me with my issues, I would really appreciate it!

---

### Post by stream303 on 2009-04-30
I just ran a quick test of glxgears on my G5 with nouveau and I get

575 Frames in 5.0 Secs = 115.010 FPS

Not sure if this is good or bad since I'm not really into graphics.

There may be an issue when installing nouveau between G4's and G5's - I'm not sure, but bluepumpkin seems to have found a cure for his G4 with nouveau:

[http://ubuntuforums.org/showthread.php?t=1137500](http://ubuntuforums.org/showthread.php?t=1137500)

---

### Post by djxfade on 2009-04-30
COuld you please give a a briefly guide howto install and set up nouveau? :)

---

### Post by stream303 on 2009-04-30
In my case, all I had to do was to do two things:

1) Download and install xserver-xorg-video-nouveau
2) Make sure that my /etc/X11/xorg.conf driver pointed to "nouveau".

Here is a snippet of my modified /etc/X11/xorg.conf:

```
Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:240:16:0"
        **Driver          "nouveau"**
EndSection
```

Your BusID may be completely different from mine!

HOWEVER, just prior to doing this, I was recompiling the original nv driver, so I had also installed the **build-essential** package, and also all the sources to nv and it's dependencies.  So I had ALL the software repositories active at the time.

I am not totally sure if this was part of reason for the success!  When installing nouveau, I did see that it was either compiling or configuring something in the background that I wasn't keeping track of - so it sat there for awhile thinking while installing it and I left it to do it's job.  I almost cancelled it because it took awhile.

What I'm wondering is if I would have been successfull if I had NOT installed the build-essential compiler elements and the nv source and it's dependencies?

Again, I'm not sure if I just lucked out because of what I was doing before the install of nouveau or if this doesn't mean anything.

NOTE: pxwpxw mentions that nouveau also installs some source, so maybe just making sure that the Ubuntu sources repository is active before doing this is the catch....

---

### Post by djxfade on 2009-05-01
I did as you mentioned, (on a fresh 9.04 install).
Activated the source repository, and installed build-essentials.
Then i ran sudo apt-get install xserver-xorg-video-nouveau.

This is what happended when it started to compile the modul.

```
Adding Module to DKMS build system
Doing initial module build

Error! Bad return status for module build on kernel: 2.6.28-6-powerpc (ppc)
Consult the make.log in the build directory
/var/lib/dkms/nouveau/0.0.11+git20090404/build/ for more information.
dpkg: error processing nouveau-kernel-source (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of xserver-xorg-video-nouveau:
 xserver-xorg-video-nouveau depends on linux-nouveau-modules; however:
  Package linux-nouveau-modules is not installed.
  Package nouveau-kernel-source which provides linux-nouveau-modules is not configured yet.
dpkg: error processing xserver-xorg-video-nouveau (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          ldconfig deferred processing now taking place
Errors were encountered while processing:
 nouveau-kernel-source
 xserver-xorg-video-nouveau
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by stream303 on 2009-05-01
Huh, Bluepumpkin seemed to have to do this but on a G4 - not sure why this seems to fail on G4's and not the G5's:

> Well I did a bit more searching around and poking around the make.log and I found the solution

Apparently it can't find crtsavres.o in /usr/src/linux-headers-2.6.28-6-powerpc/arch/powerpc/lib, so I found it in /usr/lib/gcc/powerpc-linux-gnu/4.3 and copied it over.

So anyway, this worked for me:

```
sudo cp /usr/lib/gcc/powerpc-linux-gnu/4.3/crtsavres.o  /usr/src/linux-headers-2.6.28-6-powerpc/arch/powerpc/lib
```


And just to make sure, you also have these checked in synaptic or manually downloaded:

libdrm-nouveau1
and
nouveau-kernel-source

I would think that xorg-server-nouveau would pull these down automatically as dependencies, but best to check..

---

### Post by robyinno on 2009-06-23
In fact this:
> sudo cp /usr/lib/gcc/powerpc-linux-gnu/4.3/crtsavres.o  /usr/src/linux-headers-2.6.28-6-powerpc/arch/powerpc/lib

Solve the problem even in my case.(PowerBook 12 1 ghz)

If you have already installed nouveau is needed to remove and then reinstall after have make the copy.

In my case the /etc/X11/xorg.conf doesn't exist so I have put this:

> # xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:0:16:0"
        Driver 		"nouveau"
	Option 		"Randr12" "on" 
	Option          "AccelMethod"   "EXA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

