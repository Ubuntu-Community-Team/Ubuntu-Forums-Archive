---
title: "increasining linux partition size"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by ICEcoffee on 2007-11-26
I have several partitions on my system scattered over 3 HDD's (I think):

* WinXP
* WinXP restore partition
* PClinuxOS 2007
* various pre-existing Windows OSes (no longer installed)
* A Previous Ubuntu 7.10 OS (which got screwed up so I installed another)
* My Current and active Ubuntu 7.10 OS

My current and active Ubuntu OS is almost out of space. Ubuntu allocated itself about 15GB at  install,  and I have used nearly 93%, in only 6 weeks. I am happy to loose partitions of previously installed OSes in order to give Ubuntu more space, but I want to keep the WinXP partition and the backup WinXP partition. What is the best and SAFEST way to do this?

---

### Post by mahiyar on 2007-11-26
Load live CD, from there use GParted to get the desired partitons. However remember to take a printout of the current layout (sudo fdisk -lu), and before hand keep a plan ready as to how and what you are going to do.

---

### Post by -grubby on 2007-11-26
well if you're not using the "previous Ubuntu 7.10" than I suggest you just resize over that space

---

### Post by CatKiller on 2007-11-26
> **ICEcoffee said:**
> What is the best and SAFEST way to do this?

Read what you're doing carefully. Research if you aren't sure. Back up any critical information before you begin.

Defragment any Windows partitions you want to keep. This will make the process slightly quicker, and potentially slightly safer.

Use either your Ubuntu live cd or the GPartEd live cd to re-arrange your partitions - you can't edit an already mounted partition.

Check /boot/grub/menu.lst and /etc/fstab after you're done to change anything that needs changing if you've altered the partition order at all, so that they can find the correct partitions.

Good luck!

---

### Post by fineas on 2007-11-26
Maybe the "sudo apt-get clean" command can help free up some space.For more information check this:[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html), especially 3.6 Removing unused package files: apt-get clean and autoclean

---

### Post by ICEcoffee on 2007-11-26
My current, live Ubuntu lives in SDB3, so do I just use one of these partition managers to delete the other partitions, minus the ones I want to keep? Don't I then have to allocate the freed up space to SDB3 or do I have to tell Ubuntu that the space is there?

---

### Post by AlanRogers on 2007-11-26
> **CatKiller said:**
> Defragment any Windows partitions you want to keep.Can I poke my nose in and add 'thoroughly' to that? The built in defragmentation utility in Windows XP won't defrag the drive completely in one pass; it needs multiple passes to be effective.
 
Only when you have as big a blue block to the left-hand side as you can get would I consider using the Live CD on an NTFS partition and then only after I'd rebooted and defragmented the drive another five times. The suggestion to back up important data should be followed too.
 
I attach screenshots from my work computer. It took three runs just to make this much difference!

---

### Post by ICEcoffee on 2007-11-26
Thank everyone. It all seems rather scary, it's a shame Ubuntu isn't friendly and powerful enough for me just to talk to it (as in Star trek Next Gen) and ask it to delete relevant partitions and then allocate free space to Ubuntu. But if it were that easy, we wouldn't have any nerds/geeks.

Thanks again, I'll do my best and see what happens.

---

### Post by AlanRogers on 2007-11-26
> **ICEcoffee said:**
> It all seems rather scary, it's a shame Ubuntu isn't friendly and powerful enough for me just to talk to it.Here, you have a forum to ask questions of, answers freely given and Live CDs to make it happen. I wasn't and am still not aware of any such equivalent in Windows. Ergo, when sorting out Windows problems, I use Linux Live CDs! BTW, [Knoppix]("http://www.knoppix.org/") is about the best for this; all required tools immediately available.

---

