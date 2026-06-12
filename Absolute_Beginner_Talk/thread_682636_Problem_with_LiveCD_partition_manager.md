---
title: "Problem with LiveCD partition manager"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by xzin on 2008-01-30
I tried to resize my Ubuntu partition with the liveCD partition manager, but I get this error when I try to do it:

e2fsck -f -y -v /dev/sda1
/dev/sda1 is mounted.
e2fsck 1.40-WIP (14-Now-2006)
e2fsck: Cannot continue, aborting.

Looks like the partition I try to resize is mounted, even though I unmounted it with the partition manager. And why is it mounted in the first place if I'm using the LiveCD?`
Oh, and I'm using Ubuntu 7.04 LiveCD, but I have 7.10 installed.  I already tried resizing the partitions with the Gparted liveCD, but it just gave me error during the boot. Downloaded it from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by aeiah on 2008-01-30
all partitions get mounted with the livecd so you can browse files and whatnot. its a shame the gparted livecd doesnt work for you because i find it far more convenient and up to date than the ubuntu livecds. anyway, have you tried unmounting the partition with the umount command in a terminal (when using the livecd)? or right clicking on the partition and selecting to unmount it? it might be worth trying that before anything else since its the simplest thing to check. i know you said unmounting via the partition manager didnt work but perhaps within nautilus or via the terminal it will

---

### Post by mikeyphi on 2008-01-30
> **xzin said:**
> I tried to resize my Ubuntu partition with the liveCD partition manager, but I get this error when I try to do it:

e2fsck -f -y -v /dev/sda1
/dev/sda1 is mounted.
e2fsck 1.40-WIP (14-Now-2006)
e2fsck: Cannot continue, aborting.

Looks like the partition I try to resize is mounted, even though I unmounted it with the partition manager. And why is it mounted in the first place if I'm using the LiveCD?`
Oh, and I'm using Ubuntu 7.04 LiveCD, but I have 7.10 installed.  I already tried resizing the partitions with the Gparted liveCD, but it just gave me error during the boot. Downloaded it from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

LiveCD will mount the psrtitions to let you have a 'full' play with the system!
Have you tried using the Ubuntu LiveCD and unmounting the partition before running gparted?

---

### Post by xzin on 2008-01-30
Thank you, I unmounted the partition with right-clicking on it, and now it seems to be working.
Resizing at the moment, I'll tell you if I get more problems. :KS

e: Yeah, the problem was with trying to unmount the partition with the partition manager, much easier without it.

---

