---
title: "DVD Drive"
date: 2005-05-11
forum: Absolute Beginner Talk
---

### Post by garnertr on 2005-05-11
Greetings,

Found this forum and thought I'd hang out here... first off, Love Ubuntu, out of the several distro's I've found, so far outstanding, right down my level! (low!!)

Anyway, my biggest issue is my Alienware Area 51m Sentia 177Mhz laptop the installation doesn't recognize my installed DVD R/RW / CD drive.

The drive is fine, brand new, worked 100% under Windows, Red Hat (Fedora) and a few other Linux Distros.

What I cannot figure out is, what can I do to get ubuntu to recognize the drive, is there some way to force a recheck of hardware?  I'd hate to reinstall, I've got the system to where I like it, but if I must I must... I've done it before! :)

any thoughts?

---

### Post by defkewl on 2005-05-11
Could ypu please show your /etc/fstab here?

---

### Post by garnertr on 2005-05-11
Per you requets:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0



PS - you guys are great, thanks for the quick response!  i've gotten XINE to work and am happy w/ the results of that, also, Totem had sound/no picture and VLC had picture but no sound... go figure! :)

thank you

---

