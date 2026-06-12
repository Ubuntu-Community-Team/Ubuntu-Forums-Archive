---
title: "cd/dvd will not mount"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by princeofchildren on 2008-01-14
hallo, 

I am new to linux, I have gutsy 7.10 installed on a PC. when I try to open a cd or dvd it says "cannot mount volume", this problem arose after I edited the fstab file to get my external ntfs hard drive working, well, now that that works the cd wont mount. I would greatly appreciate any advice.

fstab file:
in bold is the bit that fixed my external HD

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
**# /dev/sdb1/media/EXTERNAL ntfs-3g defaults,force 0 0**
UUID=916a3b3e-fdbb-4b60-9c67-ecc795cef2a5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1976375f-4fc6-4a2f-bc67-bbed4dfa6de9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,auto,exec 0       0# 

thanks,
-D

---

### Post by mattismyname on 2008-01-14
Have you followed the instructions at the url below for getting the restricted dvd decoder SW?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mrphud on 2008-01-14
try putting this into your fstab

```
/dev/sdb1/media/EXTERNAL nfts default 0 1
```

and remove all of that uuid crap. be sure to remove the # sign infront of the above code

---

### Post by princeofchildren on 2008-01-14
hi, I downloaded the restricted dvd decoder SW, when that did not work I edited the fstab file to look like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1/media/EXTERNAL nfts default 0 1
UUID=916a3b3e-fdbb-4b60-9c67-ecc795cef2a5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1976375f-4fc6-4a2f-bc67-bbed4dfa6de9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,auto,exec 0       0# 

now the cd drive does not even show up in my computer

exactly what is "that uuid crap" mrphud? and what what are the # symbols for? I have been using ubuntu for less than a week so please be patient with me.
please help.

thanks,
-D

---

### Post by princeofchildren on 2008-01-14
I got the cd to mount, but there are a few problems, here's the code:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1/media/EXTERNAL ntfs-3g defaults,force 0 0
UUID=916a3b3e-fdbb-4b60-9c67-ecc795cef2a5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1976375f-4fc6-4a2f-bc67-bbed4dfa6de9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,auto,exec 0       0

I got this when I tried to copy a file to the desktop:
Error "I/O error" while copying "/media/cdr...of2 3-.mp3".

when I try to eject, I get this:
You are not privileged to unmount the volume '070717_01'.

I guess I'll just keep messing with it, but I have no idea what I'm doing.

---

