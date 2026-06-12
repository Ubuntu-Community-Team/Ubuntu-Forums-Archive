---
title: "CD/DVD mount problems using sata drive under 7.10"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by wheelie77 on 2007-10-28
Hey Guys,

I have having a real hard time trying to get my ubuntu set up nice becuase for some strange reason i can automatically mount a dvd but not a cd? I have a poineer sata dvd/cd combo drive which i hope is not the problem? anyway, here is my fstab config : 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=92fa672e-9eef-41ac-b3e7-7031142a2553 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=cd1204c6-5615-4387-8cac-629405bdc505 none            swap    sw              0       0
#/dev/scd0       /media/cdrom   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom   auto,iso9660 user,noauto,exec 0       0
/etc/fstab (END)

PS: i don't use cd's much any more but i need to run a virtual win xp for development ;-(

Cheers

---

### Post by wheelie77 on 2007-11-11
Does anyone read these forums, or am i wasting my time asking questions here?

thanks wheelie

---

### Post by warren.stanley on 2007-11-11
similar issue - any thoughts folks ??

---

### Post by NotTheMessiah on 2007-11-13
I'm not going to be of much help(hope you've solved your problems) - i am able to mount CD's but here is my fstb file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=9c28f29b-295e-4dac-b0cd-fee7c02fd0c0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=98de0b8f-76a0-41f6-86bd-8af98386b0be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by wheelie77 on 2007-11-21
Thanks !Messiah,

I did have a go at you configuration and still no luck :(. Anyway, I have almost given up as it seem that the "community" that is so profound, is not really much of a community at all when you have to fix everything your self??

Cheers

---

### Post by Sukarn on 2007-11-22
I'm having a similar problem (I think), but for me, my dvd drive was initially detected when I installed ubuntu 7.04 64-bit, but after upgrading to 7.10, the drive is missing from /dev so it does not auto mount, neither can it be manually mounted.

---

