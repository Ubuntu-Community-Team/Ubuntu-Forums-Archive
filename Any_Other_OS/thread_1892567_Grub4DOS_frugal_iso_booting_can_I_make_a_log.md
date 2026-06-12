---
title: "Grub4DOS frugal iso booting can I make a log?"
date: 2011-12-08
forum: Any Other OS
---

### Post by nooby on 2011-12-08
There are several error on red flashing by when boot. 
I wish there where an easy way to either make a text file 
or a way to stop booting and write the warning down on a paper. 
I do trust that one of them say something rather similar to this one 

getpwuid_r(): failed due to unknown user id (0 ...

Maybe not exactly like that but rather similar. 

I boot using this code. I tried to add debug to it but had no knowledge how

 title  Linux Mint 12 RC works ramdisk_size=1048576 root=/dev/ram
 find --set-root --ignore-floppies --ignore-cd /linuxmint-12-gnome-dvd-32bit-rc.iso
 kernel	/LM12/casper/vmlinuz rw  file=/cdrom/preseed/mint.seed boot=casper iso-scan/filename=/linuxmint-12-gnome-dvd-32bit-rc.iso ramdisk_size=1048576 root=/dev/ram noeject noprompt 
 initrd	/LM12/casper/initrd.lz
   

Sure I can sit with Smartphone and try to catch it but I am a slow guy and the camera has a delay too so not sure if it is practical. 

So if you know how one can get a file by adding some code to the kernel like that tell the boot to make an error file that would be cool.

---

### Post by Perfect Storm on 2011-12-08
Moved to Other OS/Distro Talk.

---

