---
title: "Unable to install: Grub won't load"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Booji on 2007-05-18
I tried twice to install 7.04 daily last night and failed. Here's my specs:

Boot Order:
cdrom: Primary Master NTFS
IDE: Secondary Master, boots from here, has XP data files
SATA1: 1st Partition NTFS, WinXP, 2nd Partition FAT32, 3rd Partition EXT3, 4th Partition, /swap

I have a ATI 9800 video card

I couldn't boot the live cd at all until I used daily build 4/14 (or something). Live CD works great. On install, I had it install Grub to IDE secondary master MBR. On reboot, it said something like "starting grub", then the system hangs. Recovered using fixboot, fixmbr. Tried another install and tried to put Grub on the SATA MBR (figuring I could just switch boot order in the bios)  and it said "failed installing grub." I have in the \boot\grub folder is device.map:
(hd0)	/dev/hdc
(hd1)	/dev/sda

I am only in Windows right now (at work remoted in), but I can see \etc\fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=2ba18459-0ab4-4df5-a3ac-c636ec32f66d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc1
UUID=D610B07710B06063 /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=48B01CFFB01CF562 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=E2C9-9C1E  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=d533c5f2-c1be-4632-beaf-0d16935ff725 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

With no menu.lst or anything else in \grub, what do I need to do? I would prefer to use grub on the IDE HDD to choose between Windows and Ubuntu.

Would this work better is I installed onto the IDE HDD?

Thanks,

---

### Post by Najand on 2007-05-18
What do you mean by CDROM as the first master Harddisk?
What is the order of your booting devices in your BIOS and what is the output of:
```

sudo fdisk -l

```

---

### Post by Booji on 2007-05-18
> **Najand said:**
> What do you mean by CDROM as the first master Harddisk?
What is the order of your booting devices in your BIOS and what is the output of:
```

sudo fdisk -l

```

I have no idea why I have the cdrom on the Primary Master, I just noticed it looking in the bios (and I built this machine). I'm afraid if I move it my drive letters will change and it will screw up windows (since it boots off of C: but windows is installed on D:). I'm at work, I'll do the fdisk when I'm back at my pc tomorrow. Thanks.

---

### Post by dstew on 2007-05-18
Don't change any drive settings. Your boot drive appears to be /dev/sda (the drive with the XP partition on it). You need to install grub to the MBR of this drive. In device.map, it shows that grub names this drive (hd1). In grub-speak, the linux root partition, which should contain the /boot/grub directory, is probably (hd1,5). Grub starts counting from 0, so /dev/sda6 would be (hd1,5).

Boot the live CD, open a terminal window, and start grub (type **grub**). You should get the grub shell prompt:```
grub>
```Enter the command:```
grub>find /boot/grub/menu.lst
```This returns the location of the grub root partition. In your case it will probably be (hd1,5). Use the result of this command as grub's root, and re-install grub:```
grub>root (hd1,5)
grub>setup (hd1)
grub>quit
```You might have to edit /boot/grub/menu.lst in order to get all your os's to boot properly, but hopefully this will get your Ubuntu install working. If your boot drive was /dev/hdc, then you would use the same commands except **setup (hd0)**. Note that the grub disk id numbers can be changed if you change any bios settings, such as boot order. So, it is possible (depends on the bios) that if you change the setting to boot /dev/sda, it might now be (hd0). Then, grub's root would not be set right. It is always best to leave the disk boot order alone, install Ubuntu, and fear not to put grub into the MBR of whatever drive is the boot drive.

---

### Post by Booji on 2007-05-18
dstew:

The HDD boot order is set to the IDE drive first, and that is where the ntldr and boot.ini reside. If I change the boot order so the SATA drive is first, XP won't boot, so that's why I think the IDE (hd0) is the boot drive. Also, I don't have a menu.lst, just devices.map in that directory - grub failed to install the second go around (when I told it to install to sda). Also, the second time it did not detect my Windows install. Is the fact that I am booting off of C (hd0)  but windows is on E (hd1) screwing things up? Or is having my cdrom as primary master bad?

Thanks, you folks are quick. I won't be home to try the suggestions until tomorrow, but then I *really* want to get a working install. If it weren't for my fiance begging me not to get rid of Word, I'd dump XP all together: I use it all day at work and am so tired of it.

---

### Post by dstew on 2007-05-18
The menu.lst file is not created by grub, but by the Linux installer. What I mean by installing grub is setting it up to boot. The Linux installer creates the /boot/grub menu, and puts into it the grub stage1, stage2, menu.lst and device.map files. If there is no menu.lst file there, it suggests that something is wrong with the Linux installation itself. Did you try the grub>find /boot/grub/menu.lst command just to see if it is in there somewhere? Did you make a separate /boot partition, or do you only have the one Linux root partition? To see your file system as it really is, boot the Live CD and enter:```
sudo fdisk -l
```The fstab file may not be an accurate depiction of your current situation, only the situation that was present at the time you installed Linux.

---

### Post by sailor2001 on 2007-05-18
tell gf  that OPEN OFFICE is much better than word.......and it is

---

### Post by Booji on 2007-05-19
I couldn't get that install to boot at all. I tried all the options on the Super Grub Disk, but no luck. So I just repartitioned my C: drive and installed there, figuring it might be easier. Install went fine and booted after I removed "splash" from the boot line. Thanks for all the quick help,

---

