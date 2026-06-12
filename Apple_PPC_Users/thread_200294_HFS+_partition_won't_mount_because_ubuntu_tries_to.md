---
title: "HFS+ partition won't mount because ubuntu tries to mount it as ext2"
date: 2006-06-20
forum: Apple PPC Users
---

### Post by n00bWillingToLearn on 2006-06-20
If I try to mount my HFS+ partition (/dev/hda3) in disks-manager it shows up as ext2 and does not mount when I click enable but doesn't give an error message either. But if I ```
sudo mount -t hfsplus /dev/hda3 /media/machd
```it mounts fine and if I go back to disks-manager it now says that the file system is "unknown".

---

### Post by BoneKracker on 2006-06-20
That's weird.  I don't like that disk-manager thing.

It looks like you've got it set up right in the fstab.

What does it say when you
```
cat /etc/mtab
```

Have you rebooted or run

```
sudo mount -a
```
(you might have to unmount it first)

That might refresh the "disk manager".

---

### Post by onehotcutey on 2006-06-20
Yeah I don't think the disk mounter can properly detect the hfs or hfs+ partitions.

I set up my fstab to automatically mount the partition, I would assume that so long as the fstab is setup up correctly you could then use the disk mounter to mount the drive.

I'll post the line from my fstab when I get home later.

---

