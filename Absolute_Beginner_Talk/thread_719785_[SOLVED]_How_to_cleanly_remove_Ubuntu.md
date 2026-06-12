---
title: "[SOLVED] How to cleanly remove Ubuntu?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2008-03-09
Just need to know the best way to remove Ubuntu without disturbing my Vista install.

---

### Post by maniac_X on 2008-03-09
fix your **VISTA MBR** [(link)]("http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html") and then delete the swap/ext3 partitions using something like [PartedMagic live CD]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.News"). If you fix your MBR first you shouldn't have any GRUB errors on the next boot up.

.

---

### Post by Rocket2DMn on 2008-03-09
You can either wipe the partitions using the LiveCD or GParted LiveCD, or even from windows (though I'm not sure it would see the swap at all...).  Using GParted from either CD should allow you to "grow" your windows partition to use up the newly freed space that was occupied by Ubuntu.  
Deleting the partitions will probably break GRUB though, but you can restore the windows bootloader by putting in your windows cd, booting to it, entering the recovery console and running
```
fixmbr
```
Then GRUB will be gone.

As always, make sure all your stuff is backed up before fiddling with partitions.

---

### Post by Papa-san on 2008-03-09
Gotcha!

Thanks!

---

### Post by myddewji13 on 2008-03-09
how do i do this (ie fix the mbr) if vista came preinstalled on my computer?-ie no cd... i have recovery disks but that puts it back to factory settings (all my apps get uninstalled/i have to update again :( )

---

### Post by Rocket2DMn on 2008-03-09
myddewji13, I quick forum search revealed a couple of links to this method: [http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

---

### Post by myddewji13 on 2008-03-09
thnk u so much

---

