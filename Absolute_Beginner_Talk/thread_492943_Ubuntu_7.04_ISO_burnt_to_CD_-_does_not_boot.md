---
title: "Ubuntu 7.04 ISO burnt to CD - does not boot"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by OzzMosiz on 2007-07-05
Ok, I had issues with my Ubuntu 7.04 install as I installed Win XP on the other partition and now I can't get dual boot working (booting from Ubuntu 6 disk and getting to a command prompt grub could not find any device).

So I download Ubuntu 7.04d again and rip onto CD, not my PC does not want to boot from any disk I burn it too!

I hate this! :(

---

### Post by splintercellguy on 2007-07-05
How are you burning the CD? Make sure you're burning it as an image, not burning it as a new bootable CD/data CD compilation.

---

### Post by OzzMosiz on 2007-07-05
splinter just doing that now. Probably the mistake I was making. The more I get wound up the more mistakes I make! :)

The Bourbon is coming out tonight that's for sure!!

---

### Post by bigken on 2007-07-05
also burn it as slow as possible

---

### Post by az on 2007-07-05
> **OzzMosiz said:**
> Ok, I had issues with my Ubuntu 7.04 install as I installed Win XP on the other partition and now I can't get dual boot working (booting from Ubuntu 6 disk and getting to a command prompt grub could not find any device).

So I download Ubuntu 7.04d again and rip onto CD, not my PC does not want to boot from any disk I burn it too!

I hate this! :(

Grub could not find device?  The cd boots with isolinux, not grub.  If there is no disk in the drive, can you boot normally into windows?

---

### Post by OzzMosiz on 2007-07-05
Az, could boot from Ubuntu 6 but not ubuntu 7 - burned the ubuntu 7 wrong. - sorted now.

I got it working and repaired Grub (partially) - when trying to boot from my previous Ubuntu installation I now see "Error 17: Cannot mount selected partition"

I've booted from the CD and gone through some of the install process and it only see's the entire disk. Windows see 4 partitions (2 large and 2 small)
Can anyone advise? I don't want to have to reformat with Ubuntu and then re-install both Windows XP and Ubuntu all over again if I can avoid it.

---

### Post by orb9220 on 2007-07-05
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)
[http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub)

---

### Post by OzzMosiz on 2007-07-05
Orb, gone through most of the processes on those pages, except for mounting the linux partition. I don't know what the device ID is. I do know that Grub tried to boot from hd0,2 not sure what that maps to in terms of device ID /dev/????

---

