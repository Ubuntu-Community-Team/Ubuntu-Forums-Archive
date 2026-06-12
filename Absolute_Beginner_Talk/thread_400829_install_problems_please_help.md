---
title: "install problems please help"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by RiPPeR777 on 2007-04-04
ok i have i have an AMD 64-bit dual core processor and 2 BFG 7800 gt nvidia grafix cards and 2 gigs of ram. i download the AMD 64-bit version of Ubuntu 6.10, copied the image onto a disk and tryed to install it but after  i hit install on the innicial boot up screen it loads then i guess try to show the install procedure screen but, it looks like it freezes and makes a quick buzz with the ubuntu logo all fuzzed out. i was woundering if it was my grafics card. and if so how do i fix it. and if not what the hell do i do?

---

### Post by DSn0wMan on 2007-04-04
The most likely scenario is that you have a bad iso burnt to disk. Make sure to check the MD5sum of the downloaded iso, then check it again after you have burnt it to disk.

edit: this may be helpful [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by tonyr1988 on 2007-04-04
What speed did you burn the disc at? If you burn at a high speed, there is a VERY good chance there are errors (this isn't special for Ubuntu - it's just how fast burning works...). If there's a single error, it will not work properly.

Also, if you're going to use the AMD64 version, be aware of the limitations. You can also use the plain old i386 if you'd like (it will work just as well). A very useful link:

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

In the end, the choice is up to you. Just make sure you know the pros and cons.

---

### Post by Dual Cortex on 2007-04-04
Donwload the 32 bit version and save yourself some headaches... and even possibly forgetting the Linux world.

---

### Post by tonyr1988 on 2007-04-04
Well, you'd want the AMD64 version if you're doing a lot of CPU-intensive tasks, like encoding, ripping, editing video or audio, etc. (and are willing to work to get it going).

If you're not doing a TON of those things, stick with i386 (and burn slow, like 2X or 4X)

---

### Post by RiPPeR777 on 2007-04-04
thanx for the info guys. ok ill make burn another image at a slow speed. one more question though i thought that i needed to install the 64-bit version becasue the i386 wouldnt work with it if so yea i realy wouldnt mind not using true 64-bit instead of simulated

---

### Post by RiPPeR777 on 2007-04-04
oh and one other thing. you guys say it must be the disk but i did disk check before i tryed to install it and it said it was fine thats why i  i didnt come to the conclusion that it was the disk

---

### Post by TwistesdTexan on 2007-04-04
32 bit will work and usually with a lot less headache.

---

### Post by RiPPeR777 on 2007-04-04
nice to know

---

### Post by RiPPeR777 on 2007-04-04
another problem i have is that when i tried installing ubuntu last time it deleted my windows boot sector and used the grub loader instead but when i deleted unbuntu b/c it didnt work it deleted the grub loader so i install windows again to get my other windows app to load b/c i am using a dual boot so before i try to install ubuntu i want to be sure it will work before i delete the other windows partition

---

### Post by tonyr1988 on 2007-04-04
> **RiPPeR777 said:**
> another problem i have is that when i tried installing ubuntu last time it deleted my windows boot sector and used the grub loader instead but when i deleted unbuntu b/c it didnt work it deleted the grub loader so i install windows again to get my other windows app to load b/c i am using a dual boot so before i try to install ubuntu i want to be sure it will work before i delete the other windows partition
AFAIK, Ubuntu won't touch your Windows boot sector. What it does is affect the MBR (Master Boot Record), which tells it which boot sector to load. Windows' MBR boot loader is called NTLDR. The one Ubuntu uses is GRUB. If you need to restore your NTLDR (if you have to uninstall Ubuntu again), it's not necessary to completely re-install Windows.

Simply put in your Windows install disc and choose to Repair. When you get to an MS-DOS console, type:

> FIXMBR

Restart, take out CD, and you should go.

Hopefully you won't have to uninstall Ubuntu again, though. :)

---

### Post by RiPPeR777 on 2007-04-04
thanx that will save me alot of hasle. anyway i have be looking though the form and i have found alot of people having the same problems as me. so far i figured it is my video card. but all the steps i have taken have yet to work. after the inicial grub loader splash screen it freezze to a black screen. i have taken steps to try to fix it but nothing has yet worked.

1.after pressing F6 loading the boot options and deleting "quiet splash" and adding "single  vga=791(disables grafical interface)
2.sudo dpkg-reconfigure -phigh xserver-xorg (just let me change allowed resolutions)
3.sudo apt-get install nvidia-glx (this worked well i thought it whent online and installed drivers i think)
4. sudo nvidia-glx-config enable ( enables new drivers is what im guessing)
5.then after i thought everything was all good i whent to chck and see if the grub editor new what grafics card i had by typing "pico /etc/x11/xorg.conf" but nothing showed up in the window so im guessing ubuntu has no idea what grafix card im using.

please help!!!!!!!!!!!

---

### Post by Dual Cortex on 2007-04-04
Remember Linux's case sensitivity.
pico /etc/**X11**/xorg.conf

---

### Post by RiPPeR777 on 2007-04-04
oh so x11 is really X11. ill try it and see what happens

---

### Post by RiPPeR777 on 2007-04-04
ok that worked i found the devices and changed nv to vesa but still doesnt work

---

