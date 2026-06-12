---
title: "Is this what my /etc/fstab output is supposed to look like?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by IHeartLinux on 2007-03-19
I'm still trying to get my DVD player to work right, with no luck.

I've been searching the forums for ANYTHING that could possibly help me figure out how to get things working...I found a link to the Enabling a DVD-ROM page on wiki.freegeek.org, but I'm still having trouble figuring out how to get things working.  This page assumes that the DVD-ROM is a stand-alone item, while mine is a CDRW/DVD combo drive, and I'm not sure how to alter the instructions for my situation.

Anyhow, when I run /etc/fstab, this comes up.

root@jess-laptop:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       none            swap    sw              0       0
/dev/sda1       /media/cdrom0   udf,iso9660 user,noauto     0       0

Is this what it's supposed to look like?  I thought the cdrom was supposed to come up as /dev/cdrom or /dev/dvd?  HELP!  I feel like such a dunce when it comes to this...*facepalm*

If this is any help, my computer is an IBM Thinkpad T30, dual-booting WinXP and Kubuntu.

---

### Post by Bachstelze on 2007-03-19
There certainly is a problem with the CD-ROM since it's expected to be at the same device note than your FAT32 partition. What's the output of this ?

 ```
ls /dev/hd?
```

---

### Post by IHeartLinux on 2007-03-19
root@jess-laptop:~# ls /dev/hd?
/dev/hda  /dev/hdc

---

### Post by ScouseMouse on 2007-03-19
I am having the same problem, I originally had installed a CD player which mounted correctly, then I changed it for a DVD player, which is not being mounted.:confused: 

My fstab output is as follows

/dev/hdc  /media/cdrom0  udf, iso9660 user, noauto

But hdc is not listed in the dev directory.

Sorry for butting in on your message

---

### Post by Kateikyoushi on 2007-03-19
What do you have in /dev for me the dvd is scd0.

---

### Post by mcduck on 2007-03-19
I'm pretty sure that correct device for your CD/DVD drive is /dev/hdc. (with no partition number) Anyway, it most likely is not /dev/sd?? as those are SATA/SCSI drives.

---

### Post by mcduck on 2007-03-19
> **ScouseMouse said:**
> I am having the same problem, I originally had installed a CD player which mounted correctly, then I changed it for a DVD player, which is not being mounted.:confused: 

My fstab output is as follows

/dev/hdc  /media/cdrom0  udf, iso9660 user, noauto

But hdc is not listed in the dev directory.

Sorry for butting in on your message

If you plugged it into different cable/connector than where the old drive was it's now either /dev/hdb or /dev/hdd.

hda is the first connector in first IDE channel, hdb is second connector in first IDE, hdc is first connector in second IDE channel and hdd second connector of second channel.

For SATA drives the device comes straight from the connector used, first SATA connector is sda, second is sdb and so on.

---

### Post by ScouseMouse on 2007-03-19
I used the same cable and connector.  Here is my fstab output

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc      /media/cdrom0   udf,iso9660 user,noauto     0       0

Checked the dev directory and there is no meantion of either hdb or hdd.  Only listings are for hda,hda1,hda2,hda5. Should I see them listed in the etc directory?:confused:

---

