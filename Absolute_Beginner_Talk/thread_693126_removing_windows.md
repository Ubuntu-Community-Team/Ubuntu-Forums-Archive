---
title: "removing windows"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by emtjr928 on 2008-02-10
Well I am finally ready to make my Windows partition go away. I started with a windows 2000 installation, made a dual boot with Dapper and now have a dual boot with Gutsy with Vmware running Windows 2000. I have done some of it and here is my fdisk -l


Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92619261

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         788     6329578+   7  HPFS/NTFS
/dev/hda2            1217       14593   107450752+   f  W95 Ext'd (LBA)
/dev/hda3             789        1216     3437910   83  Linux
/dev/hda5            1217        6068    38973658+  83  Linux
/dev/hda6            6069        8601    20346291   83  Linux
/dev/hda7            8602        8729     1028128+  82  Linux swap / Solaris
/dev/hda8            8730       14593    47102548+  83  Linux

Partition table entries are not in disk order

hda1 is windows
hda2 is extended logical partition
hda3 and hda5 are empty partitions
hda6 root
hda7 swap
hda8 home

What would be the most simple way to get rid of windows without messing up Grub or the MBR that I assume is on hda1

I know that I can do a clean install saving /home, but I din't know if that would affect my VM or the settings I had to do to get nvidia running. The live cd does not like my card.

Thanks
Ed

---

### Post by Rocket2DMn on 2008-02-10
Are you able to use the [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/")?  You can boot into that and delete the windows partition.  You probably won't be able to add the fresh space t to your root filesystems since it doesn't seem to be next to it, so maybe just format it as ext3 and use it as a data partition.  You will have to edit /etc/fstab as well (since it should be set to mount that partition as ntfs) - ask if you need help with that.
If GRUB fails to load, here is how you can reinstall GRUB without the use of the LiveCD, it uses the Super Grub Disk instead - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-f5b2b33b369cf4e319ad0f1df557c42290ba2d33](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-f5b2b33b369cf4e319ad0f1df557c42290ba2d33).

---

### Post by Majorix on 2008-02-10
You don't have a bootable linux partition. That will be a problem :)

---

### Post by Rocket2DMn on 2008-02-10
> **Majorix said:**
> You don't have a bootable linux partition. That will be a problem :)

That's why I gave the option to reinstall GRUB :).  It's not a problem, just an inconvenience.

---

### Post by emtjr928 on 2008-02-10
I follow most of that and I do have gparted live and Supergrub cds.

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92619261

Device Boot Start End Blocks Id System
/dev/hda1 * 1 788 6329578+ 7 HPFS/NTFS
/dev/hda2 1217 14593 107450752+ f W95 Ext'd (LBA)
/dev/hda3 789 1216 3437910 83 Linux
/dev/hda5 1217 6068 38973658+ 83 Linux
/dev/hda6 6069 8601 20346291 83 Linux
/dev/hda7 8602 8729 1028128+ 82 Linux swap / Solaris
/dev/hda8 8730 14593 47102548+ 83 Linux

Partition table entries are not in disk order

hda1 is windows
hda2 is extended logical partition
hda3 and hda5 are empty partitions
hda6 root
hda7 swap
hda8 home

Could I and if so how would I end up with the following:

four primary partitions
eliminate hda 1,2,3 and format as one primary partition ext3 for media storage
leave root, swap and home intact.

By the way I have never edited /etc/fstab

Thanks
Ed

---

### Post by Rocket2DMn on 2008-02-10
You can just delete the hda1, 2 and 3 partitions from GParted and format that space as one partition with ext3.  You can include hda5 in that if you want since you say it's empty.  This will work only if the partitions are next to eachother physically on the disk (you'll just have to try).
Please make sure you have your important data backed up first since fiddling with partitions has the potential to be dangerous.
After you reinstall GRUB (which you will probably have to do), we can help you with fstab.  Do your repartitioning, get past GRUB and get into Ubuntu, then post your /etc/fstab file along with the output of ```
sudo fdisk -l
``` and we will help you get it right.
Good luck!

---

### Post by emtjr928 on 2008-02-10
Ok I removed 3 and 5. 2 is an extended LOGICAL partition and gparted live won't let me do anything to it. Anyway I rebooted and grub would not load. Tried supergrub with no success. I switched to my old video card so that I could boot live cd and post my situation. Evidently during my different upgrades and such grub was installed on partition 5 which I deleted.
Any help before I do a fresh install while maintaining my old /home.
thanks
Ed

---

### Post by Rocket2DMn on 2008-02-10
Since you have the LiveCD functioning, you can use that to reinstall GRUB: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4)

---

### Post by emtjr928 on 2008-02-10
Here is my current fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92619261

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         788     6329578+   7  HPFS/NTFS
/dev/hda2            1217       14593   107450752+   f  W95 Ext'd (LBA)
/dev/hda5            6069        8601    20346291   83  Linux
/dev/hda6            8602        8729     1028128+  82  Linux swap / Solaris
/dev/hda7            8730       14593    47102548+  83  Linux

When I try to boot linux from GRUB I get an error 17 can't mount

Foung grub stage 1 (hd0,4) so I pointed there. setup hd0 

Not sure how to look at my real /etc/fstab to show you what may be wrong

Still in live cd for now

---

### Post by Rocket2DMn on 2008-02-10
Maybe you should just reinstall since your partitions are still sorta screwed up.  Wipe everything except your /home partition (looks like it's at hda7 now).  You had so many partitions it had to use logical partitions, that gets to be a major hassle, it's probably just as easy to start fresh.  You should be able to do all the wiping from the LiveCD (just delete the correct partitions and make them empty space).

---

### Post by emtjr928 on 2008-02-11
Ok I reinstalled gutsy and got the new empty partition to mount at boot. However the owner and group of the file which is mounted as /media/storage is root.
I have tried the following with no luck:
 sudo chown emtjr928:emtjr928 /media/storage
sudo chmod 664 /media/storage
where emtjr928 is my user and group

Ubuntu runs fine and boots correctly but I have yet to install my best video card and reconfigure x until I work this other problem out.
Any help would be appreciated
Thanks
Ed

---

### Post by stchman on 2008-02-11
Unless you are really lacking in hdd space just leave Windows there.  You never know when you are going to need it.  I leave XP on my system and use it very rarely.  It takes up about 25G of my 250G hdd.

Windows is a tool, albeit a poor one but it does have it's uses like GAMING.

---

### Post by emtjr928 on 2008-02-11
Windows is gone. Formatted the space as ext3 to use for media file storage. Just can't get the ownership or permissions set so I can use it although it does mount correctly at boot.

---

### Post by emtjr928 on 2008-02-11
Stchman,
Looked at your resource website and followed your instructions there for new ext3 partition. I've got happy feet.

Thank you

---

### Post by Rocket2DMn on 2008-02-11
To get your partition to mount correctly, it needs a good fstab entry.  Can you post the outputs of:
```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by emtjr928 on 2008-02-11
Rocket2Dmn,
I changed the fstab entry for the partition with the following paramaters:/media/storage ext3  auto,defaults,rw  0   0

Then I :sudo chown -R (username:username) /media/storage
Then I:sudo chmod -R 755 /media/storage
Finally: sudo mount -a      

Reboot and the partition mounted correctly and I can read, write, create folder etc.

Thanks for the follow up.
Now to reconfigure x again later when I have time to use my newer video card and I'll  be done tinkering. Right LOL

---

