---
title: "[SOLVED] Permanently enable swap file?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Wynne G Oldman on 2007-10-24
Hi. after moving Gutsy from a 36 GB HDD to a 146GB HDD with Acronis TI, I find that when I boot, and look at System Monitor, my swap file isn't enabled. I loaded Gparted, and selected swap on, and when I look in System Monitor again, it shows it as enabled. So far, so good. Only problem is, is when I reboot, it's not enabled again. I tried doing the same thing by booting with the Gparted Live CD, and the same thing happens. Any Ideas?

---

### Post by Pumalite on 2007-10-24
[http://ubuntuforums.org/showthread.php?t=528306](http://ubuntuforums.org/showthread.php?t=528306)

---

### Post by Wynne G Oldman on 2007-10-24
> **Wynne G Oldman said:**
> Hi. after moving Gutsy from a 36 GB HDD to a 146GB HDD with Acronis TI, I find that when I boot, and look at System Monitor, my swap file isn't enabled. I loaded Gparted, and selected swap on, and when I look in System Monitor again, it shows it as enabled. So far, so good. Only problem is, is when I reboot, it's not enabled again. I tried doing the same thing by booting with the Gparted Live CD, and the same thing happens. Any Ideas?Sorry, my mistake. I said swap file. I meant swap partition. I'm new to all this!:)

---

### Post by steve.horsley on 2007-10-24
Can you post the output of the commands 
**sudo fdisk -l**
and 
**cat /etc/fstab**

You probably need some changes to fstab, and fdisk will tell us where the swap partition is.

---

### Post by Wynne G Oldman on 2007-10-24
> **steve.horsley said:**
> Can you post the output of the commands 
**sudo fdisk -l**
and 
**cat /etc/fstab**

You probably need some changes to fstab, and fdisk will tell us where the swap partition is.Hi. This is the output of the first command.

Disk /dev/sda: 146.8 GB, 146814976000 bytes
255 heads, 63 sectors/track, 17849 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d1d92d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17120   137516368+  83  Linux
/dev/sda2           17121       17849     5855692+   5  Extended
/dev/sda5           17121       17849     5855661   82  Linux swap / Solaris

Disk /dev/sdb: 36.7 GB, 36703918080 bytes
255 heads, 63 sectors/track, 4462 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf244f244

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4340    34861018+   7  HPFS/NTFS
/dev/sdb2            4341        4462      979965   1c  Hidden W95 FAT32 (LBA)


and the second command

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b0717b2d-6d13-450d-99f3-e6273bc033ba /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e966a605-eca0-4080-a278-1f6308f6c7b9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by steve.horsley on 2007-10-24
It looks like it is configured to use swap. But it is configured to use a swap partition with the label e966a605-eca0-4080-a278-1f6308f6c7b9. I forgot to ask for the output from the command blkid. But I guess that's the label from your previous swap partition. Try using the proper device reference instead. Try changing the line:
```
UUID=e966a605-eca0-4080-a278-1f6308f6c7b9 none swap sw 0 0
```
to this:
```
/dev/sda5 none swap sw 0 0
```

---

### Post by Wynne G Oldman on 2007-10-24
> **steve.horsley said:**
> It looks like it is configured to use swap. But it is configured to use a swap partition with the label e966a605-eca0-4080-a278-1f6308f6c7b9. I forgot to ask for the output from the command blkid. But I guess that's the label from your previous swap partition. Try using the proper device reference instead. Try changing the line:
```
UUID=e966a605-eca0-4080-a278-1f6308f6c7b9 none swap sw 0 0
```
to this:
```
/dev/sda5 none swap sw 0 0
```Thank you very much. That worked perfectly! I've also learned a few things tonight. I've never edited fstab before, so I first tried to do it with Gedit, from the menu. It wouldn't let me save it. So I ran it from Terminal with the sudo command and it worked. I rebooted, but nothing had changed, so I opened up fstab again and noticed that the line I had edited and some others had a "#" in front of them.  I thought that maybe this served the same purpose as "rem" in a DOS batch file, so I removed the "#" rebooted, and my swap partition is now enabled. Many thanks again.:)

---

### Post by steve.horsley on 2007-10-25
Well done. Yes, I was perhaps making assumptions that you know how to do thise things.

When starting graphical apps, you shouls use gksudo rather than just sudo though. Something to do with the handling of GUI access permissions, and using sudo can leave a rogue file (Xauth or something like that?) that prevents further GUI apps launching. gksudo always cleans it up.

---

