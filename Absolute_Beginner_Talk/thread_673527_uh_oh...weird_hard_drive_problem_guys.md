---
title: "uh oh...weird hard drive problem guys"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by sleeper414 on 2008-01-20
hi there.
earlier today i created a thread about having to mount my heard drives everytime...and with the hlep of the friendly gods, it was fixed.

however, after shutting don the tower to attach a new keyboard, my most important drive, with 99% of my music and photos is "unable to mount"
it is listed as read only.

if i boot back into windows(yuck) it opens and reads everything fine.
will somthing like automatix fix this?

this happened once before, but, ubuntu gave me possible causes. i had to perform a 'disk chk' in windows, then it worked fine in ubuntu, no such luck time.
help!!!

---

### Post by LaRoza on 2008-01-20
Unable to mount AND read only?

Post the output of:

```

cat /etc/fstab

```

and:

```

sudo fdisk -l

```

EDIT: What format is the drive?

---

### Post by sleeper414 on 2008-01-20
its NTFS (3.1)

isnt there somthing like a driver to fix it?

---

### Post by sleeper414 on 2008-01-20
those codes didnt work.....

---

### Post by stevescripts on 2008-01-20
> **sleeper414 said:**
> those codes didnt work.....

You *did* run them from a terminal?

the output should resemble this (from my opensuse10.3 box)

```

steveo@linux:~> cat /etc/fstab
/dev/disk/by-id/scsi-SATA_WDC_WD800JB-00J_WD-WMAM98050666-part5 /                    ext3       acl,user_xattr        1 1
/dev/disk/by-id/scsi-SATA_WDC_WD800JB-00J_WD-WMAM98050666-part6 /home                ext3       acl,user_xattr        1 2
/dev/disk/by-id/scsi-SATA_WDC_WD800JB-00J_WD-WMAM98050666-part2 swap                 swap       defaults              0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
steveo@linux:~> su root
Password: 
linux:/home/steveo # fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00091b04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   83  Linux
/dev/sda2              14         141     1028160   82  Linux swap / Solaris
/dev/sda3             142        9729    77015610    f  W95 Ext'd (LBA)
/dev/sda5             142        2752    20972826   83  Linux
/dev/sda6            2753        9729    56042721   83  Linux


```

Please try again and post back - somebody should be able to help

Steve

---

### Post by sleeper414 on 2008-01-21
the  "cat" code says 'bad command or file name.

the "sudo code" says the same thing....weird.

i will try again.

im certian it has to do with some script to automount the hard drives, everything worked fine before that.

and i know it has to do with NTFS too.
ok..ive had to much coffee.

ill get back to work

---

