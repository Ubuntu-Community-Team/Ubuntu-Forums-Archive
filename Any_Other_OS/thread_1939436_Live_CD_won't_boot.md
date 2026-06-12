---
title: "Live CD won't boot"
date: 2012-03-11
forum: Any Other OS
---

### Post by Devster on 2012-03-11
I know this isn't technically ubuntu... 
I've tried with a Zorin Os .iso and linux mint, but no matter what I do, when I burn an iso to a CD it loads the splash screen (that says automatic boot in x seconds) and then will not finish booting. If I run it in compatibility mode it gets to /casper/initrd.lz and hangs there.
I'm trying to load linux mint 12 lxde cd 32bit, but it does the same thing with a zorin OS CD. And if I try to use a USB it just gives me a black screen with 'Boot error'. 

Any idea what's going on?

---

### Post by Bölvaður on 2012-03-11
If this is the same problem I had few years ago (when I had SysLinux problems... for some reason I cannot remember) then this should work.
[QUOTE="http://askubuntu.com/questions/34088/cant-install-with-usb-pen-drive-syslinux-problem"]


There are reports that you can fix the bug by opening syslinux.cfg on the USB drive and replace the following line:

```
ui gfxboot bootlogo
```
with

```
gfxboot bootlogo
```[/QUOTE]


// added
if this will not work then check if you are trying to install 32bit OS on a 32bit CPU or 64bit OS on a 64bit CPU.
I think the motherboard will complain about wrong architecture if you have 32 bit computer and have 64 bit operating system on the usb. But just in case... check it.

---

### Post by Perfect Storm on 2012-03-12
Moved to Other OS/Distro Talk.

---

