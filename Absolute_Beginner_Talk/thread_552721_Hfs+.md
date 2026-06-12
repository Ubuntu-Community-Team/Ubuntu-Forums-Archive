---
title: "Hfs+"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by etomic13 on 2007-09-16
so I wiped my iBook of OS X a week ago to dabble in ubuntu. Now I need to go back to OS X and I deleted everything on the disc its all unallocated and im running off a live cd. I tried to create a new partition and it needs to be HFS+ but I can't create that in gpart. So what do I do now. All OS X recognizes is hfs/hfs+ and hfs is too small.

---

### Post by SpiritIsReality on 2007-09-17
howdy
I used advanced search, keywords hfs+ osx reinstall, searched forum apple ppc users.
got this
[http://ubuntuforums.org/showthread.php?t=545245&highlight=hfs%2B+osx+reinstall](http://ubuntuforums.org/showthread.php?t=545245&highlight=hfs%2B+osx+reinstall)
hope it helps

trails

---

### Post by etomic13 on 2007-09-17
Thanks for the reply, I did all of that, but when I try to go into disc utility off my instal disc it lists no hard drives in the left column and it just says gathering disc information, I let it sit and do that for about an hour with no avail.

---

### Post by SpiritIsReality on 2007-09-17
howdy
have to hope someone who knows the answer shows up

trails

---

### Post by SpiritIsReality on 2007-09-17
howdy
maybe post in the apple ppc forum as well
trails

---

### Post by SpiritIsReality on 2007-09-17
howdy
found this howto resize hfs+
it resizes smaller, hopefully be able to enlarge your small hfs+
[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)

found by this search
[http://www.google.ca/search?hl=en&q=create+hfs%2B+%22live+cd%22+-%22boot+camp%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=create+hfs%2B+%22live+cd%22+-%22boot+camp%22&btnG=Search&meta=)
[http://forum.insanelymac.com/lofiversion/index.php/t32890.html](http://forum.insanelymac.com/lofiversion/index.php/t32890.html)
there's also this from gentoo
[http://ubuntuforums.org/archive/index.php/t-454674.html](http://ubuntuforums.org/archive/index.php/t-454674.html)
[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

sorry for your rough road, hopefully smoother sailing ahead

trails

ryan723 ...thanks

---

### Post by ryan723 on 2007-09-18
> so I wiped my iBook of OS X a week ago to dabble in ubuntu. Now I need to go back to OS X and I deleted everything on the disc its all unallocated and im running off a live cd. I tried to create a new partition and it needs to be HFS+ but I can't create that in gpart. So what do I do now. All OS X recognizes is hfs/hfs+ and hfs is too small.

OSX "Disk Utility" should still see other partitions on a device (I know it sees my ext3 partitions).

> Thanks for the reply, I did all of that, but when I try to go into disc utility off my instal disc it lists no hard drives in the left column and it just says gathering disc information, I let it sit and do that for about an hour with no avail

If OSX cannot detect the drive at all, I would consider a hardware problem.  I would try booting off your linux CD and make sure that the drive is still detected there. 

If you can see the drive in linux, you may want to repartition and reformat....maybe OSX is having trouble reading the existing partition table?  If it is not hardware related, then you may find much more help on a Mac forum, as this seems to be an OSX issue.

I think you can also use the OSX install disk's Terminal.app to run the Apple command line fsck and fdisk, etc. which should be way more verbose than Disk Utility.  Again, a Mac forum could be much more help.

---

