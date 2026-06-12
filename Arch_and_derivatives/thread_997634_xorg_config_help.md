---
title: "xorg config help"
date: 2008-11-30
forum: Arch and derivatives
---

### Post by AnLGP on 2008-11-30
Hello,

I can get arch up and into the part where you start using pacman to install packages but when I get to the point where I can use either the default configuration for Xorg (it doesn't work) or configure my own (I can't get that to work either) I get stuck.

I printed the beginner's guide and it says that if I have a running install with an xorg configuration I can just copy it and put it on that distro.  The only issue I can see with this is the current xorg config file is all defaults on my fresh ubuntu install:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

So that doesn't really help me when I need to configur my monitor and video card.  Any help would be appreciated.

For the record what happens after I type "startx" is I get a screen saying that the range isn't right.  I can't remember exactly what it says but it's a little blue box on my monitor.

---

### Post by kerry_s on 2008-11-30
```
Xorg -configure
```

then copy it to the right place:

**cat xorg.conf.new > /etc/X11/xorg.conf**

you really should learn to use the man pages.

**man xorg**

if you install something, you should try to read the man page before starting it in case you need to configure it first.

---

### Post by mips on 2008-11-30
What gfx card are you using?

---

### Post by AnLGP on 2008-11-30
It's an onboard graphics card.

             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0

Intel® Graphics Media Accelerator 950

    * Dynamic Video Memory Technology (DVMT) supports up to 224 MB of video memory

---

### Post by smartboyathome on 2008-11-30
Did you install xf86-video-intel? You need to install that to get the intel video drivers, at which point you can generate your xorg.conf and it should work.

---

### Post by AnLGP on 2008-11-30
I'll give it a go.  When I did the command to check my drivers I honestly didn't know what I was looking at.  That was probably part of the issue.  I noticed the name but not what I needed to put in to install it.  Thanks.

---

