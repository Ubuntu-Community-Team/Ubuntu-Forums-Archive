---
title: "External storage not visible if turned on at boot"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Bobthegoldfish on 2007-08-12
I have an enclosure with a 160 gig Seagate drive in it. I also have 2 flash drives that remain plugged in most of the time.

If I boot Ubuntu with the enclosure turned on none of my usb drives appear, either on the desktop, when I run lsusb or in fdisk. If I boot with it turned off and then turn it on, everything is fine and they all show up. The drive is recognised by the bios and is also recognised by Windows when I boot into that.

I've had a look through the forum and done a bit of searching on Google but everyone else seems to have the opposite problem from mine. Enclosure comes up in lsusb as Macpower Peripherals, Ltd and has 4 partitions on it. Any ideas?

---

### Post by kevstar31 on 2007-08-17
post /etc/fstab.

---

### Post by tango_ninja on 2007-08-17
i have a similar problem with an external hd formatted ntfs.,
i can access it temporarily with  <pmount>  but not permanent..

---

### Post by Bobthegoldfish on 2007-08-18
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=9110e2f5-347a-4579-b55b-a47d07d23de4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda8
UUID=5a4b15b7-e51e-4822-ac96-3455ecf5d49b /home           ext3    defaults        0       2
# /dev/hda1
UUID=08E0F68AE0F67D6E /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=B8D08D6FD08D34A2 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=18E0-B482  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=162a9fba-b49c-4eaa-9e2a-2eda8fea95e8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb        /media/floppy1  auto    rw,user,noauto  0       0

Taken after booting with enclosure turned on; would that make any difference?

---

### Post by Bobthegoldfish on 2007-09-14
*bump*

---

### Post by mlentink on 2007-09-14
Dunno.
I have a usb external that rarely shows up in Ubuntu on my laptop. A USB stick does show up, but only when connected at boot time. lsusb takes forever and ever and seens to hang. 
I'm going to do a bit more testing by connecting thses things to my desktop, and see what happens. Both run Feisty, btw.

I also vaguely remember seeing something about a usb bug on launchapd, but I Have to go back and search properly for it.

So in short: I have problems with usb too

Edit: That external doesn't even show in fdisk -l and obviously neither in fstab. Nowhere to be found. Just booted up int XP (yeah I know, but I need it for work)...bingo right there. Beats me...

---

### Post by kevstar31 on 2007-09-14
Post the output of **ls /dev** with the enclosure on and again with the enclosure off.

---

### Post by Bobthegoldfish on 2007-09-14
Attached

---

### Post by kevstar31 on 2007-09-14
first turn the enclosure on and restart.
as root type mkdir -p /mnt/sda1 /mnt/sdb1 /mnt/sdc1 /mnt/sdc2 /mnt/sdc5 /mnt/sdc6 /mnt/sdc7

mount /dev/sda1 /mnt/sda1
mount /dev/sdb1 /mnt/sdb1
mount /dev/sdc1 /mnt/sdc1
mount /dev/sdc2 /mnt/sdc2
mount /dev/sdc5 /mnt/sdc5
mount /dev/sdc6 /mnt/sdc6
mount /dev/sdc7 /mnt/sdc7
looking for what of these is the content of what drives type
ls /mnt/sda1
ls /mnt/sdc1
ls /mnt/sdc2
ls /mnt/sdc5
ls /mnt/sdc6
ls  /mnt/sdc7
then post what folder corresponds to what drive

---

### Post by mlentink on 2007-09-15
Strangely enough, I did a thorough disk check on the drive in Windows, and now it's back on my desktop again.

---

### Post by vanadium on 2007-09-15
Not quite strangely. Ubuntu won't mount a corrupt partition. The fsck command can be used to check file systems, including fat and ntfs, in case you do not have or want to access Windows.

---

### Post by mlentink on 2007-09-15
thx, I should've checked it earlier. It was just that it mounted fine in Windows.
The OP's problem hasn't been solved yet, however.

---

### Post by kevstar31 on 2007-09-15
> **tango_ninja said:**
> i have a similar problem with an external hd formatted ntfs.,
i can access it temporarily with  <pmount>  but not permanent..

post the command you use to mount the drive

---

### Post by Bobthegoldfish on 2007-09-15
If I have the drive on when I boot, all the drives disappear. If I then type
mount /dev/sda1 /mnt/sda1
it tells me:
mount: special device /dev/sda1 does not exist

Starting with the enclosure on and running ls /dev gets a list without ANY sdX in it

---

### Post by kevstar31 on 2007-09-16
Are you sure try **ls /dev |grep sd** to confirm.

---

### Post by logos34 on 2007-09-16
> **vanadium said:**
> The fsck command can be used to check file systems, including fat and ntfs, in case you do not have or want to access Windows.

fsck can be used for NTFS?

---

### Post by Bobthegoldfish on 2007-09-17
ls /dev | grep sd gets me ptysd and ttysd. No sdX

---

### Post by Bobthegoldfish on 2007-09-30
*bump*

---

