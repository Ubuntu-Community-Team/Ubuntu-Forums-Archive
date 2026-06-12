---
title: "Cannot get internal drive to autmount"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Foxphyre on 2007-10-25
I have two internal drives. The first (which ubuntu is installed on) has one ext3 partition (and all the trimmings for running ubuntu like swaps and extendeds) and another partition with NTFS for vista. the second drive has one 250GB partition that is NTFS. I can mount the two NTFS partitions manually in the computer folder but i want them to automatically mount when i boot. 

as far as research on this goes, i have looked all over the forums and nothing i have tried has worked. the last thing i tried was using and ntfs-3g tutorial to setup my fstab. when i add the entry for hda1 into my fstab and try to mount, it returns:

```
foxphyre@UbuntuFox:~$ sudo mount -a
fuse: failed to access mountpoint /media/WD250: No such file or directory
FUSE mount point creation failed
Unmounting /dev/hda1 (WD 250)
```

now i can't even go into the computer under places and mount it manually. im not sure what's going on here.  i havent tried adding my Vista partition to the fstab at all. i want this drive to work first before i even go there.

---

### Post by nick_h on 2007-10-25
Post a copy of your /etc/fstab.

Check that the mount point has been created.

---

### Post by MegaJim on 2007-10-25
first you need to create the mounting directory:

```
sudo mkdir /media/WD250
```

although personally i'd put it in /mnt/WD250

---

### Post by Foxphyre on 2007-10-29
created the directory for the mountpoint and it mounts just fine on reboot. thanks for the help.

---

