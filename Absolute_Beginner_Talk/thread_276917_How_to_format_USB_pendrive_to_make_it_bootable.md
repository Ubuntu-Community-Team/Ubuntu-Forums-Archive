---
title: "How to format USB pendrive to make it bootable"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by mahy on 2006-10-13
Hi guys and gals,

I want to make a bootable USB pendrive with some live distro on it, but i dunno how to format it. If you use the factory preset (or format it in windows), simply copying the files and installing syslinux won't help. I guess it's because there's no MBR. I found a thing called HP Drive Key Boot Utility, it did help (i managed to boot into Slax), but it's only for windows! It's not a very good feeling... Any suggestions how to format it in Linux (to make it bootable)? TIA

---

### Post by meng on 2006-10-13
Here's what I would try. Let's say your pendrive is recognized as /dev/sda (for argument's sake):
cd /usr/lib/syslinux
cat mbr.bin > /dev/sda

then copy the livecd, run syslinux etc.

---

### Post by mahy on 2006-10-13
> **meng said:**
> Here's what I would try. Let's say your pendrive is recognized as /dev/sda (for argument's sake):
cd /usr/lib/syslinux
cat mbr.bin > /dev/sda

then copy the livecd, run syslinux etc.

Too bad there's no such file as /usr/lib/syslinux, at least on my machine :( Yes i do have syslinux installed.

---

### Post by meng on 2006-10-13
Ah... sorry! Perhaps you could try:
whereis syslinux
to find out where the files are.

---

### Post by mahy on 2006-10-13
> **meng said:**
> Ah... sorry! Perhaps you could try:
whereis syslinux
to find out where the files are.

Sorry man, there's really no such file anywhere in the directories spat out by whereis...

---

### Post by meng on 2006-10-13
Oh man, are you SURE you have syslinux installed? ;)

---

### Post by mahy on 2006-10-13
> **meng said:**
> Oh man, are you SURE you have syslinux installed? ;)

Positive. This is contents of my /usr/lib/syslinux:

-rw-r--r-- 1 root root   408 2006-03-16 18:04 copybs.com
-rw-r--r-- 1 root root 12081 2006-03-16 18:04 img1200k.gz
-rw-r--r-- 1 root root 12327 2006-03-16 18:04 img1440k.gz
-rw-r--r-- 1 root root 12663 2006-03-16 18:04 img1743k.gz
-rw-r--r-- 1 root root 11515 2006-03-16 18:04 img720k.gz
-rw-r--r-- 1 root root 12720 2006-03-16 18:04 isolinux.bin
-rw-r--r-- 1 root root 13156 2006-03-16 18:04 isolinux-debug.bin
-rw-r--r-- 1 root root   512 2006-03-16 18:04 ldlinux.bss
-rw-r--r-- 1 root root 12332 2006-03-16 18:04 ldlinux.sys
-rw-r--r-- 1 root root 19132 2006-03-16 18:04 memdisk
-rw-r--r-- 1 root root 26756 2006-03-16 18:04 menu.c32
-rw-r--r-- 1 root root 13156 2006-03-16 18:04 pxelinux.0
-rw-r--r-- 1 root root 19532 2006-03-16 18:04 syslinux.com

hope it's enough to convince you. If not, this is the apt-get output:

Reading package lists... Done
Building dependency tree... Done
syslinux is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

That's it. Any more ideas?

---

### Post by meng on 2006-10-13
Sorry! I misunderstood your post
> Too bad there's no such file as /usr/lib/syslinux
and I must admit that my syslinux doesn't have an mbr.bin either. There is such a file on many live cd's though, PCLinuxOS is one and IIRC Knoppix is another. Puppy definitely has it. Can't recall if the Ubuntu Live cds have it.
I am embarrassed about leading you astray on the location of the mbr.bin file. I have tried out many live distro installs on pendrives, and have lost the MBR a few times, so I have some idea of what can go wrong.

---

### Post by mahy on 2006-10-14
Alrite, i downloaded original syslinux (not a deb package) and used mbr.bin from there. In fact, i did this:

1.) Opened GParted, erased everything, created one FAT16 partition
2.) mkdosfs /dev/sdb1 (that's my usb stick)
3.) syslinux /dev/sdb1
3.) cat mbr.bin > /dev/sdb
4.) copied Slax and made some modifications (as always)

It didn't help. :( The BIOS says: No operating system found... ](*,)

---

### Post by transactionlogfiller on 2006-10-14
Have a look at this

[http://syslinux.zytor.com/usbkey.php](http://syslinux.zytor.com/usbkey.php)

---

### Post by meng on 2006-10-14
I would have done the steps this way:
1, 2, 3b, 4, 3a (i.e. syslinux after copying files, although it may not make a difference)
and there's an option
syslinux -a /dev/sdb1
which improves compatibility/bootability for dicky BIOS.

Did your modifications include moving the /boot files to / (with respect to the stick)? [www.pendrivelinux.com](www.pendrivelinux.com) covers this.

Having said all that, I found SLAX for some reason to be inconsistent when it comes to booting on different computers, and when it doesn't work, that's the error I get. I haven't noticed this with other distros (Knoppix, PCLinuxOS, Puppy).

---

### Post by mahy on 2006-10-14
> **meng said:**
> Did your modifications include moving the /boot files to / (with respect to the stick)? [www.pendrivelinux.com](www.pendrivelinux.com) covers this.

Yes, that's exactly what i did. Look, i already managed to boot Slax from my USB in the past. The problem is that an old version of that HP formattig tool no longer works for me and i can't get a new to do what i want. I'm a bit disappointed with all of this. I don't think adding some parameters to syslinux will help, coz back then it wasn't necessary. Anyway, i'll try puppy as well, just tell me whether or not is there any other way than burning a CD first.

EDIT: I let the HP tool create an official HP rescue disk, didn't work but at least there was no error message, just a black screen with blinking cursor. So i reinstalled syslinux with many various options, including the full set (-sfma). Nothing worked.

Geez, i wish USB booting was more popular! There's so little info out there...

---

