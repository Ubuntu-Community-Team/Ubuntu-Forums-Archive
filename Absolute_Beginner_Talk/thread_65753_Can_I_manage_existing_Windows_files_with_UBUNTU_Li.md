---
title: "Can I manage existing Windows files with UBUNTU Live?"
date: 2005-09-14
forum: Absolute Beginner Talk
---

### Post by fredblow on 2005-09-14
More very newbie questions.

Having crossed the hurdle of getting UBUNTU Live CD to work at all (and having played Mahjongg for a few minutes to show myself it was really able to do something :-)), I am wondering if/how I can see existing existing Windows files in NTFS partitions, and (hopefully) copy/move them between different partitions/Hard drives.

I have 2 hard drives, one with 3 partitions, the other with 2.  Via UBUNTU Device manager, I can see 4 volumes on one drive, 3 on the other.  I presume that the extra volume on each drive is Windows drive info.

When I click on any of the volumes I get nowhere.  A friend has told me that I will need to "mount" these volumes before I can see inside them.  How do I do that?  

And once the volumes are mounted, will I be able to copy/move files in such a way that Windows would recognise the new files?

TIA.

---

### Post by aysiu on 2005-09-14
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)
[http://ubuntuguide.org/#mountunmountfat](http://ubuntuguide.org/#mountunmountfat)

---

### Post by Nequeo on 2005-09-14
[QUOTE=fredblow]More very newbie questions.

Having crossed the hurdle of getting UBUNTU Live CD to work at all (and having played Mahjongg for a few minutes to show myself it was really able to do something :-)), I am wondering if/how I can see existing existing Windows files in NTFS partitions, and (hopefully) copy/move them between different partitions/Hard drives.

I have 2 hard drives, one with 3 partitions, the other with 2.  Via UBUNTU Device manager, I can see 4 volumes on one drive, 3 on the other.  I presume that the extra volume on each drive is Windows drive info.

When I click on any of the volumes I get nowhere.  A friend has told me that I will need to "mount" these volumes before I can see inside them.  How do I do that?  

And once the volumes are mounted, will I be able to copy/move files in such a way that Windows would recognise the new files?

TIA.[/QUOTE]
 First thing to bear in mind is that NTFS is a propriety Microsoft file format, and they are not interested in letting us Linux users use it for free.

There have been attempts by the linux community to reverse engineer the NTFS format, and they are getting better. So far, Linux can read from NTFS hard-drives, but cannot write to them.  For free, anyway. If you really need to write to NTFS partitions from Linux, there's software around you can buy for about $70 american that will do the trick.

Anyway... getting back to the task at hand, simply reading/opening files on an NTFS partition is no trouble.

See [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows) for instructions on how to mount NTFS drives.

Cheers,

---

### Post by gord on 2005-09-14
as a note you might want to look into having another partition somewhere with FAT32 installed on it, both windows and linux can read/write this file system just fine.

---

### Post by FLeiXiuS on 2005-09-14
You could also use ext2, windows has an ext2 project which will allow read/write access.  :-)  Quite nifty.  

[http://uranus.it.swin.edu.au/~jn/linux/](http://uranus.it.swin.edu.au/~jn/linux/)

---

### Post by fredblow on 2005-09-16
Thanks to all of you who pointed me to the user Guide.

That should keep me very quiet for several weeks at least!    :roll:

---

