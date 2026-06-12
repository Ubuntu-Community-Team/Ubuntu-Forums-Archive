---
title: "Partition full after resize"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by f-h on 2006-11-21
Hello,

this is what i've done:

- turned the swap partition off (swapoff -a)
- resized the swap partition using gparted from nearly 3GB to 500MB
- unmounted hda2 (ext3 partition which was before the swap, not the one with ubuntu)
- resized hda2 over 11GB to 14GB (more less)
- reboot

Now the problem is that gparted shows that hda2 is 14GB and all full, system/administation/disks shows 13,8GB - all full, and 'df' command shows an old size and data on the partition:
/dev/hda2             11922836  11317092        96 100% /media/media
(11GB 100% full).

My question is, what can i do? I would like to have this 14GB partition with 2GB of free space.

Thanks in advance

---

### Post by f-h on 2006-11-22
I've found the solution, so here it is (for hda2 partition):

sudo umount /dev/hda2
sudo e2fsck -f /dev/hda2
sudo resize2fs /dev/hda2
sudo mount /dev/hda2

For main partition with Ubuntu you should probably do it from live CD.

---

