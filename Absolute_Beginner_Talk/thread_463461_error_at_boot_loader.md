---
title: "error at boot loader?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by dink1000 on 2007-06-03
hello.

i'm a newbie so i'd like to give it a try before i completly remove XP.

now so i moved all my stuff from my sata hd with the intension to use it for linux.

booted from the cd everything ok but got an error at the end of the installation

i've included some pics that might help and point out where i messed up

[pic 1]("http://homepage.ntlworld.com/jonathan.thomas4/linux/Screenshot.png")

[pic 2]("http://homepage.ntlworld.com/jonathan.thomas4/linux/Screenshot-1.png")

[URL="http://homepage.ntlworld.com/jonathan.thomas4/linux/Screenshot-2.png"]pic 3
[/URL]

i'm trying to install unbuntu on (sdc) and winblows is on (sda) but it doesn't show the two partitions:-?

---

### Post by ugm6hr on 2007-06-03
I think the problem is trying to install Grub on sda1,0.  I can't remember exactly how Grub references HDs and partitions - but it is different to Linux.  Besides which, sda1 is a partition, so sda1,0 doesn't reflect any location at all.  And it's not possible to put Grub in a non-linux partition supernode (i.e. it has to be on the MBR if you want it to replace the Windows bootloader).

I suspect that Ubuntu has probably been installed on sdc OK.  It is just missing Grub to access it now.  You need to install Grub to sda MBR, or otherwise, if you want to play it safe, do some research on Grub4DOS to access it.

---

### Post by dink1000 on 2007-06-04
so i'd put (sda) in the boot loader window instead of (hd0)?

---

### Post by dstew on 2007-06-04
I think you should put (hd0) into the boot loader window. That will put grub into the Master Boot Record (MBR) of your first disk, which I assume is the one the one your BIOS boots. The installer knows that your Linux root partition is /dev/sdc1, so it will configure grub properly.

---

### Post by dink1000 on 2007-06-04
yeah but when i tried to install with (hd0) in the boot loader screen the install finished with no problems but it booted straight into xp.

so i set bios to boot from the drive i installed ubuntu to and it said it coundn't find it

---

### Post by annda on 2007-06-04
first, boot from the live cd and make sure grub has been installed

this is a comprehensive guide to installing/recovering grub from live cd:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

in case it's not useful for you (say, grub didn't get installed at all), you can try supoergrub - there's a lot of info on hermanzone:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

