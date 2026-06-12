---
title: "[PPC] Nouveau video driver rocks on G5 iMac!"
date: 2009-04-25
forum: Apple Hardware Users
---

### Post by stream303 on 2009-04-25
One more cheer for Jaunty 9.04 for making it easy to run nouveau instead of the nv video driver.

In the past on my G5 iMac, I had to manually recompile the nv driver to take care of some geometry issues specific to my box that couldn't be resolved with simple xorg.conf editing.

Along comes Jaunty 9.04 and the easy availability of the nouveau driver.  Gave it a shot by merely installing it with synaptic, and then making sure that it would run by changing my **/etc/X11/xorg.conf**

```
Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:240:16:0"
        **Driver          "nouveau"**
EndSection
```

(Your BusID will most likely be different from my G5 iMac..)

After a restart - yeah baby!!

One less thing to deal with on my ppc box.

Thanks to the nouveau team and ubuntu for solving a really nagging problem on my system.  Recompiling the nv driver was getting to be a major chore.

Rock on!

---

### Post by joshdudeha on 2009-04-26
I have a Power Mac G4 with an nVidia card and I tried installing this driver through synaptic but I get the error:

```
"E: nouveau-kernel-source: subprocess post-installation script returned error exit status 3
E: xserver-xorg-video-nouveau: dependency problems - leaving unconfigured"

```

Could someone help me install this please?
Does it let you enable desktop effects when this is installed?

---

### Post by stream303 on 2009-04-26
On my system, actually three things got installed and were visibly checked in synaptic:

xserver-xorg-video-nouveau

libdrm-nouveau1

nouveau-kernel-source

I'll have to read the wikis to see if libdrm and the kernel source are necessary, although I'll bet they are...

---

### Post by joshdudeha on 2009-04-26
Yeah that was checked on mine too the libdrm-nouveau1

but it still fails on configuring the xserver-xorg-nouveau

---

### Post by bluepumpkin00100001 on 2009-04-26
Same happens for me on my G4.
I did a lot of searching around, but I haven't found a solution (yet, at least...)

---

### Post by pxwpxw on 2009-04-26
Thanks for that -
 
So far so good on powermac G5 SP1.6G DVI display, fixed the 1% right shift nuisance.

Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty
Linux g5 2.6.28-6-powerpc64-smp 

pxw@g5:~$ sudo aptitude  install xserver-xorg-video-nouveau

xorg.conf
Section "Device"
	Identifier "nouveau driver"
	Driver "nouveau"
EndSection

pxw@g5:~$ lspci | grep VGA
0000:f0:10.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200 Ultra] (rev a1)

It also installed  nouveau-kernel-source and libdrm-nouveau1
Depends: libc6 (>= 2.4), libdrm-nouveau1 (>= 2.4.4), xserver-xorg-core (>= 2:1.5.99.901),
         linux-nouveau-modules

pxw@g5:~$ dpkg -L  xserver-xorg-video-nouveau
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/xserver-xorg-video-nouveau
/usr/share/doc/xserver-xorg-video-nouveau/copyright
/usr/share/doc/xserver-xorg-video-nouveau/changelog.Debian.gz
/usr/share/man
/usr/share/man/man4
/usr/share/man/man4/nouveau.4.gz
/usr/share/bug
/usr/share/bug/xserver-xorg-video-nouveau
/usr/lib
/usr/lib/xorg
/usr/lib/xorg/modules
/usr/lib/xorg/modules/drivers
/usr/lib/xorg/modules/drivers/nouveau_drv.so
/usr/share/bug/xserver-xorg-video-nouveau/script
pxw@g5:~$ 

pxw@g5:~$ glxgears
586 frames in 5.0 seconds = 117.082 FPS
(I get wrong colors in glxgears, same as with driver nv).

---

### Post by stream303 on 2009-04-27
It also fixes the problem I had trying to log into the forums here where the search box would prevent me from logging in with my username unless I initially made Firefox fonts really small so that I could get the cursor into it, login, and then return the screen to normal.

With nouveau, I can login like everyone else without having to resort to display resizing tricks.

I think the forum ops thought I was crazy when I first reported this a few years ago. :)

Thanks NouVeau!

---

### Post by stream303 on 2009-04-27
Just a quick note about how I stumbled upon trying nouveau ...

I was trying to recompile the nv driver, and royally messed it up (although I did fix the geometry problem!) but ended up with some really bad colors.  BUT, I had all the repos enabled, and was able to practically blindly click my way through synaptic to get the xserver-xorg-video-nouveau package installed.

Before a reboot, I used a virtual terminal to edit my /etc/X11/xorg.conf to make sure that the "nouveau" driver would be forced, and tada!

Watch your spelling with "nouveau" btw. :)

---

### Post by bluepumpkin00100001 on 2009-04-28
Well I did a bit more searching around and poking around the make.log and I found the solution :D

Apparently it can't find crtsavres.o in /usr/src/linux-headers-2.6.28-6-powerpc/arch/powerpc/lib, so I found it in /usr/lib/gcc/powerpc-linux-gnu/4.3 and copied it over.

So anyway, this worked for me:
```
sudo cp /usr/lib/gcc/powerpc-linux-gnu/4.3/crtsavres.o /usr/src/linux-headers-2.6.28-6-powerpc/arch/powerpc/lib
```

---

### Post by hanzomon4 on 2009-04-29
So glad to see this project actually producing something useful. Can't wait for 3d support.

---

### Post by conal on 2009-05-29
Hi Folks, just did all this stuff, Nouveau seemed to install ok. I notice the font at log in is slightly corrupted but otherwise no change.

I tried to enable desktop effects but it says "desktop effects cannot be enabled" 

Where from here? and suggestions?

Thanks in advance

Conal

---

