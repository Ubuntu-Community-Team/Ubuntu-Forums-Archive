---
title: "Problem Dual Boot Configuration"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by widowmaker03 on 2007-12-18
Greetings All,
I'm brand new to Ubuntu and have been reading this forum.  
I just installed Ubuntu 7.10.  My problem is I can't get the Grub configured for a dual XP Pro/Ubuntu boot.  My system configuration is in my signature.   Basically, I have one HD dedicated to windows and one dedicated for Ubuntu.  I did a search and found posts about inputs into Grub.  I've renamed the hd0, 1 and 2 and the closest I've gotten was a blank hanging Startup screen.  I ran a sudo fdisk -l and got the following results:

Disk /dev/sda: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x6a7fe72f



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        1216     9767488+  83  Linux

/dev/sda2            1825       60801   473732752+  83  Linux



Disk /dev/sdb: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x1a751a74



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS



Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes

16 heads, 63 sectors/track, 1938021 cylinders

Units = cylinders of 1008 * 512 = 516096 bytes

Disk identifier: 0x3a038c96




I've set my timeout for 10 seconds.  The rest of my Grub is:
title		Ubuntu 7.10, kernel 2.6.22-14-generic

root		(hd0,0)

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=64966dc3-25f0-4f4c-8d40-6df4d38edd24 ro quiet splash

initrd		/boot/initrd.img-2.6.22-14-generic

quiet



title Microsoft Windows XP Professional

root (hd0,0)

savedefault

makeactive

#map (hd0) (hd1)

#map (hd1) (hd0)

chainloader +1



title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)

root		(hd0,0)

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=64966dc3-25f0-4f4c-8d40-6df4d38edd24 ro single

initrd		/boot/initrd.img-2.6.22-14-generic



title		Ubuntu 7.10, memtest86+

root		(hd0,0)

kernel		/boot/memtest86+.bin

quiet

---

### Post by Duck2006 on 2007-12-18
What is the error message?

With what your posted with your menu.lst and the output of 

sudo fdisk -l

i see that

> title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
#map (hd0) (hd1)
#map (hd1) (hd0)
chainloader +1


root should be (sd1,0) ie change to this

> title Microsoft Windows XP Professional
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1


I see that you are bootting from your ubuntu drive.

---

### Post by mdpalow on 2007-12-18
Previous poster said:
-------------------------------------------------------------------------------------
root should be (sd1,0) ie change to this

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1


You said root should be sd1, but then you have hd1 below. Is that a typo by any chance?

Thanks....

---

### Post by Duck2006 on 2007-12-18
> **mdpalow said:**
> Previous poster said:
-------------------------------------------------------------------------------------
root should be (sd1,0) ie change to this

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1


You said root should be sd1, but then you have hd1 below. Is that a typo by any chance?

Thanks....

Yer typo 7.10 names all drives as sd does not matter it they are sd or hd it has them as sd.

---

### Post by widowmaker03 on 2007-12-18
Duck,

I made the changes in Grub to:
title Microsoft Windows XP Professional

root (hd1,0)

savedefault

map (hd0)(hd1)

map (hd1)(hd0)

makeactive
chainloader +1

I now get..   Error 11:  Unrecognisable Boot String

Any suggestions?

---

### Post by widowmaker03 on 2007-12-19
Problem fixed!


I saw and followed instruction by Catlet in "Grub Error 13: "Invalid or unsupported executable format" post.

He posted the following recommendation:

root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

I copied and pasted in my Grub and it works!

---

