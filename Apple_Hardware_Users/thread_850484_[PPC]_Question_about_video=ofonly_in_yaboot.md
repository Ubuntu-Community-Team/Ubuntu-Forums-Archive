---
title: "[PPC] Question about video=ofonly in yaboot"
date: 2008-07-05
forum: Apple Hardware Users
---

### Post by stream303 on 2008-07-05
For many of us, putting video=ofonly in the kernel parameters at boot or in /etc/yaboot.conf is the only way to get video out of some systems.

The question is, does this parameter have any affect once X11 starts, or does the card just ignore it once it is able to work?

I have always wondered if video=ofonly is just a way to kick-start the card, or if it has any lingering affects on video performance once the gui is up?

---

### Post by Bikerbob on 2008-09-22
Well it would seem no one has an answer here. Did you ever find out anything more?

I have an 8.04 install on a 9500 with G3-400 and in the end was only able to get it to boot with the NO VIDEO checkbox on bootx which is video-ofonly.

I do get a gui up.. but it is only 640 x 480 and I am not able to adjust anything.

I have an ati mach64 video in the machine.. looking at Dmesg it sees it.. knows what it is. If I try and use it.. it comes up with an error.

There is the ATI driver, it should work .. blah blah .. but only above works.

I like you would like to know.. it got me here.. can I change anything or get somewhere once I am in Linux?

James

---

### Post by tiresia on 2008-09-22
> **stream303 said:**
> 
The question is, does this parameter have any affect once X11 starts, or does the card just ignore it once it is able to work?


Open Firmware has a Frame Buffer value for the screen (you can even set it with 'setenv fb=...'). So I guess - but I am not sure - that with video=ofonly the kernel will set that value for X ignoring what is in xorg.conf

---

### Post by pxwpxw on 2008-09-22
Not sure about video=ofonly, but for the open firmware video setting, agree with  **tiresia**, and that also reverts to low res after reset-nvram (zap pram) but can then be simply changed back by booting into macosx and restarting.
Here, the OF setting only affects the tty console video (normally and as in the install).
On g5 I get the usual 1680x1050 for X, regardless of whatever OF is doing. IDK about result if using fbdev in X, but I cant do that anyway.

---

### Post by BryannPaulaMelvin on 2008-09-22
As far as I can tell ofonly just uses a framebuffer driver to do the install

Later the installer tries to find your hardware...on mine it recognized the card as the wrong one.

I just got Ubuntu 8.04 working on my ibook 500

using the live cd was a disaster
using the alternate cd I installed 8.04 but was stuck in 800 by 600 mode on a partial screen...actually a split screen,..! 

googling for a solution I found that someone had taken a xorg.config file from a 606 live cd

I actually HAD a backup for the xorg.conf file so I used it from my 6.06 backup.

This booted and worked but left a corrupted square in part of the screen.

the "splash" during boot looked very unusal...like a cell phone I drowned actually!!

assuming the splash was a problem I revise yaboot to get rid of the splash
I used yabootconfig......careful here

Now boot is OK

HOWEVER gnome was a disaster! could not connect to SMB and several other problems.

I installed Kubuntu Desktop and then Xubuntu Desktop

I then apt uninstalled Gnome by removing Ubuntu-Dektop then gnome*

This leaves you with full Kubuntu Desktopand functioning XFCE

Xubuntu Desktop (meta) and a couple of gnome items used by it with

"remove gnome*  (wildcard removal)

Hopes some of this makes sense and helps

---

