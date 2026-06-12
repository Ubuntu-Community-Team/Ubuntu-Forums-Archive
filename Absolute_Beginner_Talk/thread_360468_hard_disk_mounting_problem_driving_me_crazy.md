---
title: "hard disk mounting problem driving me crazy"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by benner on 2007-02-13
i have just installed another hard disk to my machine and am having a problem.  gparted saw it as  unallocated even though there was an ntfs partition there with 75 gigs worth of stuff.  no matter because i planned to reformat it as ext3 anyways.  well, gparted wouldn't let me do anything to it.  errors.  i changed to another IDE connector and rebooted.  gparted saw the drive and allowed me to reformat it--which i did.  it was then labeled hdf1 so, as i read an another post on how to mount new drives, i added the following line to the end of my fstab:

/dev/hdf1   /mnt/newdisk  ext3    defaults     0 0

then rebooted to see if it was there.  it wasn't.  i opened gparted and the drive now appeared as unallocated again.  i tried to download another partition manager (qtparted) but after 20 minutes it has still failed to download.  i reboot with hiren's boot disk, load up a partition manager, reformat it again boot flag on.  restart.  it isn't there but in gparted, it appears and is editable again.  still can't access it.  reboot.  not there.  again with gparted it is unallocated.  

i don't really know what i am doing and am just going around in circles hoping that it will magically work.  stupid.  can someone help me out?

---

### Post by benner on 2007-02-13
half an hour and i can't even find someone to read it?  i figure this is an easy one.  please...  i haven't stopped fiddling with this and have made no progress.

---

### Post by Crooksey on 2007-02-13
Erm, if its unallocated there will be no partition so you will be mounting free space?

Is there a partition on the drive...

```
 sudo cfdisk /dev/hdf
```

 and make a partition.

EDIT- you dont need to reboot for it ti work, simply run

```
 sudo mount /dev/hdf1
```

---

