---
title: "Power Mac G4 IDE Controller Supporting Hard Disk &gt; 128GB?"
date: 2009-04-01
forum: Apple Hardware Users
---

### Post by jevchance on 2009-04-01
Hello All,

My question is, does the Power Mac G4 (graphite) support > 128GB IDE drives under Ubuntu? I thought this was a hardware limitation, but my Ubuntu installation sees the entire drive. Is it possible that it sees the entire drive, but can't use it all?

Here's some background:

I'm in the process of building a Power Mac G4 (graphite) file server. I downloaded and installed Ubuntu Server Hardy Heron 8.04 LTS. I have things running and configured nicely on the 80GB /dev/hda hard disk.

After I had everything configured, I cracked open the case to add a few hard disks. I added a 160GB hard disk /dev/hdb and a 120GB hard disk /dev/hdd. Afterwards I setup LVM2, created 2 PVs from the new drives (single partition on each), created a new VG, added the 2 PVs to the VG, and created a single 260GB LV from the group.

Now, I've come back to researching IDE/ATA controller cards that are compatibile with this system, and I read that apparently the onboard IDE controller on this computer doesn't support drives greater than 128GB. Of course, I read this AFTER I have everything setup and configured. However, Linux sees my 160GB drive just fine! Is it possible that it sees the drive, but can't use all of it?

Here's some output for you to peruse:
$ sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/hdb2
  VG Name               store
  PV Size               149.05 GB / not usable 19.80 MB
  Allocatable           yes (but full)
  PE Size (KByte)       32768
  Total PE              4769
  Free PE               0
  Allocated PE          4769
  PV UUID               dL57jk-IFE3-KkZL-92Rg-FAyd-8Xan-ZKG2Qw
   
  --- Physical volume ---
  PV Name               /dev/hdd2
  VG Name               store
  PV Size               111.79 GB / not usable 9.43 MB
  Allocatable           yes 
  PE Size (KByte)       32768
  Total PE              3577
  Free PE               26
  Allocated PE          3551
  PV UUID               EiT0Fd-gCDz-sYEp-b2RG-lozK-46F7-2RhDGi

$ sudo fdisk -l
/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled                1954 @ 64        (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled           153667969 @ 2018      ( 73.3G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                 2631501 @ 153669987 (  1.3G)  Linux swap

Block size=512, Number of Blocks=156301488
DeviceType=0x0, DeviceId=0x0

/dev/hdb
        #                    type name                  length   base      ( size )  system
/dev/hdb1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hdb2         Apple_UNIX_SVR2 HDB_LVM            312581744 @ 64        (149.1G)  Linux native

Block size=512, Number of Blocks=312581808
DeviceType=0x0, DeviceId=0x0

/dev/hdd
        #                    type name                  length   base      ( size )  system
/dev/hdd1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hdd2         Apple_UNIX_SVR2 HDD_LVM            234441584 @ 64        (111.8G)  Linux native

Block size=512, Number of Blocks=234441648
DeviceType=0x0, DeviceId=0x0

---

### Post by stream303 on 2009-04-03
What you are seeing is a root-partition size limitation in firmware.  Early G3 iMacs had 8gb limits, and some later models had 128gb root partition limitations.  The rest of the larger-than-eom disk can be partitioned for /home /usr etc.

This problem rears it's head when a disk much larger than oem is installed, and the linux installer will happily install to it, but if one had chosen "Guided partitioning - Use Whole Drive", after the bits are laid down on the disk, the system halts at the first reboot because the root partition is larger than these firmware limitations.

These model-specific firmware limitations for some models are something that no Linux installer to date is aware of, so one must take the reigns themselves if they have one of these particular boxes.

(Normally I recommend using smaller partitions, such as 7gb or perhaps 125gb instead of 8/128gb due to not wanting to be right on the boundary) for root.

That is why you have no problem with the original 80gb disk being bootable, and your other drives just being used for data.

Had you chosen to make the very large disk the one to be bootable, you'd have to manually partition to keep root under 128gb, and then divvy up the rest of the disk for whatever your needs are.

---

### Post by jevchance on 2009-04-03
Thanks very much for the reply.

I've taken steps to correct the situation, and based on your reply I'm glad I did.

I ordered up an ATA/SATA controller to deal with the larger drive. My root partition is on a 80GB drive, so this should work.

Thanks again for the detailed reply.

> **stream303 said:**
> What you are seeing is a root-partition size limitation in firmware.  Early G3 iMacs had 8gb limits, and some later models had 128gb root partition limitations.  The rest of the larger-than-eom disk can be partitioned for /home /usr etc.

This problem rears it's head when a disk much larger than oem is installed, and the linux installer will happily install to it, but if one had chosen "Guided partitioning - Use Whole Drive", after the bits are laid down on the disk, the system halts at the first reboot because the root partition is larger than these firmware limitations.

These model-specific firmware limitations for some models are something that no Linux installer to date is aware of, so one must take the reigns themselves if they have one of these particular boxes.

(Normally I recommend using smaller partitions, such as 7gb or perhaps 125gb instead of 8/128gb due to not wanting to be right on the boundary) for root.

That is why you have no problem with the original 80gb disk being bootable, and your other drives just being used for data.

Had you chosen to make the very large disk the one to be bootable, you'd have to manually partition to keep root under 128gb, and then divvy up the rest of the disk for whatever your needs are.

---

### Post by stream303 on 2009-04-04
My pleasure.  Just be aware of the multiple-drive-controller issue that can sometimes confuse the yaboot bootloader.

If your box does have a multiple drive controllers, (not just multiple drives - many have multiple drives with a single-controller) you may find it necessary to manually edit yaboot.conf with different UUID's or openfirmware paths than what is normally detected.  (Obviously followed by a ybin -v to make the change take affect)

Lots of fun going back in with rescue mode to edit yaboot.conf, doing ybin and so forth.

If you encounter this you may find the live-ppc sysadmin / rescue disk handy instead of just the usual rescue mode of the ubuntu installer:

[http://www.finnix.org/](http://www.finnix.org/)

Note that when encountering ppc bootloader issues I got into the habit of using a fully-qualified pathname instead of just ybin -v something along the lines of:

```
ybin -v -C /mnt/etc/yaboot.conf
```

just to make sure you don't end up ybinn'ing the wrong yaboot.conf file on a rescue or sysadmin disk rather than your own. :)

---

