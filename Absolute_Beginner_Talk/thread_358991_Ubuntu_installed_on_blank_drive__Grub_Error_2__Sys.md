---
title: "Ubuntu installed on blank drive / Grub Error 2 / System won't boot"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Mega_Fauna on 2007-02-11
[Rewritten from a previous messy posting]

Hi,

I had Ubuntu format a blank 200gig IDE drive and the system won't boot. Here is what happens:


Immediately following the Dell startup screen I get a message saying that the system doesn't recognize the primary drive 1, then Grub boots (after I hit F1 to continue) and give me "Error 2". When I go to the Dell Setup screen it recognizes the Primary Drive 0 but not drive 1, both are set to automatic.



Just in cast this helps:

ubuntu@ubuntu:~$ sudo fdisk -l


Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 24133 193848291 83 Linux
/dev/hda2 24134 24321 1510110 5 Extended
/dev/hda5 24134 24321 1510078+ 82 Linux swap / Solaris

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 24321 195358401 7 HPFS/NTFS
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$


Can someone please advise me on what to do?

Thanks,

---

### Post by Mega_Fauna on 2007-02-11
Alright, Idk how it happened, all I did different was to format the drive using gparted instead of the installer, and when the F2 Dell setup screen at boot came up, I just escaped out of it (as usual), and then, suddenly, and against all historical precedence, Ubuntu booted:-D

I did it! I'm a human being!

/jk

---

