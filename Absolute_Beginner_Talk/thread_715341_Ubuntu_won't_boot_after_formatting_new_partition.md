---
title: "Ubuntu won't boot after formatting new partition"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by hoges on 2008-03-04
Hi,
Being the brilliantly intelligent (read: moronic) person I am, I decided to format a section of free space on my HDD using Windows partitioner. Now GRUB won't boot ubuntu.

I have loaded up the live cd, and all the data is still there. I have also used fsck to check the ubuntu partition and all seems well - no reported errors.

I have also used the super grub boot cd to no avail. Does anyone have any idea of how I can fix the linux partition table without formatting ubuntu? I can still back up data and whatever, but I'd rather wait until the LTS comes out in April.

For reference I'm running 7.10/XP/Vista (xp and vista are on a separate hdd and boot fine).

Any help would be appreciated.
Cheers
Hoges

---

### Post by glennric on 2008-03-04
Follow the directions on the following link to restore grub.  That may help.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by hoges on 2008-03-04
> **glennric said:**
> Follow the directions on the following link to restore grub.  That may help.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

I followed the directions and it didn't work from the live cd. It also didn't work with super grub last night.

I'll give easybcd a shot...

---

### Post by hoges on 2008-03-04
EasyBCD didnt' work either. I'm not sure exactly what's happening. It just keeps coming up with error 17. Has anybody experienced this before or have a fix? I'm not entirely sure it is the mbr. I'm thinking something wrong with the partition table???

---

### Post by logos34 on 2008-03-05
> **hoges said:**
> EasyBCD didnt' work either. I'm not sure exactly what's happening. It just keeps coming up with error 17. Has anybody experienced this before or have a fix? I'm not entirely sure it is the mbr. I'm thinking something wrong with the partition table???

maybe formatting/creating a new partition out of the empty space on the linux drive changed the partition #s.  You might try using Gparted on the ubuntu live cd (system>admin>partitioner) to delete it and create another one in its place.  Hopefully gparted will write the changes to the part. table correctly.

On the live cd run

**sudo fdisk -l**

and post it.

---

### Post by hoges on 2008-03-05
Ok, at the moment it's not really possible to delete the files on the new partition, as they were backed up from another hdd I no longer have access to. 

So here's my fdisk -l output. Some things to note:
1) I have 3 hdd's installed
2) The one I'm having problems booting is sdc2
3) Yes, I know it's a mess :( but I'll clean it up when the LTS comes out.
4) I've no idea what sdc1 is for. What's W95?

I'm beginning to think it may be easier to just forget about it until the LTS and use windows instead.

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xc2acc2ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6772    51196288+   7  HPFS/NTFS
/dev/sda2            6773       16254    71680000    7  HPFS/NTFS
/dev/sda3           16254       41346   189691904    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28d028cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20480000    7  HPFS/NTFS
/dev/sdb2            2550       38914   292088832    7  HPFS/NTFS

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f8d0f8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         262     2104483+   f  W95 Ext'd (LBA)
/dev/sdc2   *         263        6341    48829567+  83  Linux
/dev/sdc3            6342       22947   133386240    7  HPFS/NTFS
/dev/sdc4           22947       36482   108712960    7  HPFS/NTFS
/dev/sdc5               1         262     2104452   82  Linux swap / Solaris


---

### Post by louieb on 2008-03-05
One thing to check. Ubuntu uses the **uuid **to identify partitions. Its a long string of numbers and letters. Formating a partition will change its uuid. 
You'll need to use a live CD to check and fix things.

To find what the uuid is. there are two commands you can use.
```
ls -l /dev/disk/by-uuid/
```or 
```
blkid
```or copy it into gedit
```
gedit =(blkid) &
```after you know what the uuid is you need to check two files and make sure the uuid is correct.
**/boot/grub/menu.lst **and [B]/etc/fstab

[/B] > I'm beginning to think it may be easier to just forget about it until the LTS and use windows instead.Meatloaf: [COLOR=Blue]"I would do anything for love, but I won't do that.":)[/COLOR]

---

### Post by hoges on 2008-03-05
Yes, it works!!!

While looking through the menu.lst I noticed that the grub fixes from earlier didn't actually change the root hdd location. I played around with it a bit, and for some reason it requires hd0,1 as opposed to the hd2,1 which worked previously.

The uuids were all the same. I've got a feeling that I may have installed linux on a different partition some time back, and all the grub fixes were still trying to fix the long erased mbr. Which is odd, because there was no error reported from either supergrub or the ubuntu grub fix utility...

Anyway, through all your help I can now use linux again! Thanks for the help!

---

### Post by louieb on 2008-03-06
One more thing in /boot/grub/menu.lst look for the **groot= **statement. The  updater will use whatever is there for the root statement next time there is kernel update.

---

