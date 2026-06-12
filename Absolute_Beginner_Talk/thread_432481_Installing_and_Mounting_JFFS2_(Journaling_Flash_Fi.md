---
title: "Installing and Mounting JFFS2 (Journaling Flash File System version 2)"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by kewlkartman on 2007-05-04
I am a first-time Linux user. I managed to install Ubuntu 7.x on my x86 system. I 

also got the mtd-tools package installed. I cannot figure out how to create a 

partition for JFFS2 and how to install/mount JFFS2. I am a Windows user, so 

explicit, detailed instructions will be very helpful, and highly appreciated. The 

mkfs.jffs2 file was already part of the kernel included within Ubuntu. Thanks!

---

### Post by jargoman on 2007-05-05
I've never heard of jffs2 but this just might work for mounting. 

$ sudo mount -t jffs2 /dev/hda1 /mnt/hda1

you need to replace hda1 with the location of the partition. hda1 being the first disk and first partition. hdb3 would second hard drive third partition

sorry I couldn't help you more

---

### Post by dustinharriman on 2007-09-08
If you read the man page for "mount" (try the command "man mount"), you'll see that you can mount many different kinds of filesystems, like ext3, reiserfs, etc. with the "-t" option.  

**Unfortunately jffs2 is not one of them!**  So the command above that tries to use "mount -t jffs2" is not going to work.  After creating a jffs2 filesystem on a USB flash drive, I tried to mount it myself, and I got an error message:

# sudo mount -t jffs2 /dev/sdb2 /mnt/tmp

mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Note: The mtd-tools package doesn't seem to include any utility for mounting jffs2 filesystems either.  I'm not even sure one exists.  That is to say, jffs2 may not be mountable whatsoever from userspace.

---

### Post by tags07 on 2008-02-03
It is possible..but not as easy as loopback mounting iso..

[http://www.handhelds.org/hypermail/familiar/62/6232.html](http://www.handhelds.org/hypermail/familiar/62/6232.html)

> modprobe mtdcore
modprobe jffs2
modprobe mtdram
modprobe mtdchar
modprobe mtdblock

dd if=image-jffs2 of=/dev/mtd0
mount /dev/mtdblock0 mnt 

---

### Post by runesvend on 2008-02-24
When I try to execute the command *modprobe mtdcore* I get an error saying:

FATAL: Module mtdcore not found.

I have installed the package *mtd-tools* with apt-get but it hasn't helped.

Any ideas?

---

### Post by tags07 on 2008-02-26
Check this link for more info on how to build the kernel with MTD options to build mtdcore..etc
My Ubuntu kernel came built in with all these enabled..so i didnt have to do anything

[http://maemo.org/community/wiki/ModifyingRootImage/](http://maemo.org/community/wiki/ModifyingRootImage/)

---

### Post by runesvend on 2008-03-02
Why do you think your Ubuntu kernel came with *mtdcore* built in and mine didn't? I'm running Gutsy and this is the output of *uname -a*:

Linux rune 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

I'd rather not build a custom kernel if I can avoid it :)

---

### Post by hughsw on 2008-03-07
The name mtdcore appears to have been changed to mtd.  This just worked for me on my server 7.10 system:

[FONT="Courier New"]hugh@VmUbuntu:~/gumstix-oe$ sudo apt-get install mtd-tools
...
hugh@VmUbuntu:~/gumstix-oe$ sudo modprobe mtd
hugh@VmUbuntu:~/gumstix-oe$ sudo modprobe jffs2
hugh@VmUbuntu:~/gumstix-oe$ sudo modprobe mtdram
hugh@VmUbuntu:~/gumstix-oe$ sudo modprobe mtdchar
hugh@VmUbuntu:~/gumstix-oe$ sudo modprobe mtdblock
hugh@VmUbuntu:~/gumstix-oe$ sudo dd if=gumstix-hsw-image-gumstix-custom-verdex.jffs2 of=/dev/mtd0
...
hugh@VmUbuntu:~/gumstix-oe$ sudo mkdir /mnt/gumstix/
hugh@VmUbuntu:~/gumstix-oe$ sudo mount -t jffs2 /dev/mtdblock0 /mnt/gumstix/
hugh@VmUbuntu:~/gumstix-oe$ ls /mnt/gumstix
bin  boot  dev  etc  home  lib  media  mnt  proc  sbin  sys  tmp  usr  var[/FONT]

There seems to be a size limit on the jffs2 image of 4MB which dd will bump into; presumably some parameter setting somewhere can override that....

Cheers,
-Hugh

---

### Post by hughsw on 2008-03-07
To get an 8 MB mtd0 use the following arguments to mtdram
[FONT="Courier New"]sudo modprobe  mtdram total_size=8192 erase_size=256[/FONT]

-Hugh

---

### Post by runesvend on 2008-03-16
Thanks a lot! Using *mtd* instead of *mtdcore* works perfectly.

---

