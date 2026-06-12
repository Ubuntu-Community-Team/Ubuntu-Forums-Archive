---
title: "2nd HD Help"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by mcy782 on 2008-02-05
I'm a newbie to Ubuntu and Linux. I have two HDs and installed Ubuntu successfully to one of them intending to use the second for storage. When I run ubuntu the second HD does not appear in the Computer section and I have no idea on how to find it and mount it automatically when I boot. Any help would be appreciated. Thanks.

---

### Post by csat on 2008-02-05
> **mcy782 said:**
> I'm a newbie to Ubuntu and Linux. I have two HDs and installed Ubuntu successfully to one of them intending to use the second for storage. When I run ubuntu the second HD does not appear in the Computer section and I have no idea on how to find it and mount it automatically when I boot. Any help would be appreciated. Thanks.

Try go to a console terminal and type sudo cat /etc/fstab <enter>

The result will show you what was found by Ubuntu installation process.  Look for something like /dev/sda1 or /dev/sdb1.  Possibly your second HD is defined to such lines and you can list its contents with the command of ls -al name of the device.

---

### Post by mcy782 on 2008-02-06
This is what is returned:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=24e6111f-c6d8-48b3-bc80-225af3d48837 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=baabfda4-f669-462c-b633-00d6bee81a25 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

When I run fdisk -l, I get this showing the second 40gb drive:

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000443f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3557    28571571   83  Linux
/dev/sda2            3558        3649      738990    5  Extended
/dev/sda5            3558        3649      738958+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     8217243   55  EZ-Drive


It's not picking up the second drive. Any suggestions on how to locate it?

---

### Post by hyper_ch on 2008-02-06
run

```

sudo fdisk -l

```

---

### Post by aeiah on 2008-02-06
does your bios detect the drive? it may be a problem with the hard drive or the cabling (slave/master sorta thing)

---

### Post by mcy782 on 2008-02-06
Okay, I'm making progress. My 2nd drive is now showing up in the File Browser as "37.3GB Volume Disk." When I try to access it by clicking on it, there is a file called "lost + found" (I don't have any idea where that came from) When I click on the file, I get the message "Folder Contents Could Not Be Displayed, You do not have the permissions necessary to view the files." I want to make this drive a storage drive for mp3s and such. Any suggestions on what to do next.  Thanks.

---

