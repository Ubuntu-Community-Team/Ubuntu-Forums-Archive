---
title: "Cannot Mount ANY USB Drive"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-01-17
I can't seem to mount any USB drive. I have tried a 2GB Sandisk Cruzer Micro and a generic USB drive which both can be read in XP. I have tried formatting it in FAT and FAT32 still no luck. Can anybody help please?

---

### Post by aysiu on 2007-01-17
Can you plug in the drive, paste these commands into the terminal ```
sudo fdisk -l
df -h
cat /etc/fstab
``` and then copy and paste to this thread the output of those commands?

---

### Post by syalam on 2007-01-17
syalam@syalam-laptop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           6       48163+  de  Dell Utility
/dev/hda2   *           7        5330    42765030    7  HPFS/NTFS
/dev/hda3            5331        5801     3783307+  db  CP/M / CTOS / ...
/dev/hda4            5802        7296    12008587+   5  Extended
/dev/hda5            5802        7165    10956295   83  Linux
/dev/hda6            7166        7296     1052226   82  Linux swap / Solaris

Disk /dev/sda: 2048 MB, 2048901120 bytes
255 heads, 63 sectors/track, 249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         249     2000061    b  W95 FAT32
syalam@syalam-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5              11G  3.2G  6.7G  32% /
varrun                244M   72K  244M   1% /var/run
varlock               244M     0  244M   0% /var/lock
procbususb             10M  148K  9.9M   2% /proc/bus/usb
udev                   10M  148K  9.9M   2% /dev
devshm                244M     0  244M   0% /dev/shm
lrm                   244M   18M  227M   8% /lib/modules/2.6.17-10-generic/volatile
/dev/hda1              47M  7.3M   40M  16% /media/hda1
/dev/hda2              41G   26G   15G  64% /media/hda2
/dev/hda3             3.7G  3.2G  453M  88% /media/hda3
syalam@syalam-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=be6d0266-9971-4cec-89e8-c2a9d076003d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=07D5-0717  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=E0B06CA0B06C7EC2 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=be6b7d01-c4a0-47c8-bcbb-de5e2400b77d none            swap    sw              0       0
/dev/sda1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
syalam@syalam-laptop:~$

---

### Post by aysiu on 2007-01-17
Maybe it's because /dev/sda1 is defined in the /etc/fstab file as being a CD-ROM?

---

### Post by syalam on 2007-01-17
Ohh, I see. My CD-ROM drive does not actually function. Is there a way I can disable this? Or is there a way I can specify something else other than sda1 for my flash drive? I am new to linux, so please bear with me.

---

### Post by aysiu on 2007-01-17
Let's try this. Unplug your USB drive.

Back up your /etc/fstab file first: ```
sudo cp /etc/fstab /etc/fstab.backup
``` Edit the /etc/fstab file ```
gksudo gedit /etc/fstab
``` Comment out the /dev/sda1 line. In other words, change it from looking like this ```
/dev/sda1 /media/cdrom0 udf,iso9660 user,noauto 0 0
``` to looking like this ```
#/dev/sda1 /media/cdrom0 udf,iso9660 user,noauto 0 0
``` The # sign basically means *ignore the rest of this line*. Then save and exit. Finally, reboot.

Then, plug your USB drive in again. Please report back whether it works or not. If it doesn't we'll try something else, I guess.

---

### Post by syalam on 2007-01-17
My desktop seems to have disappeared. I can't access hda1, hda2 or hda3 anymore. I tried restoring fstab back and restarting but no luck. Its still messed up. when I try and run fstab from the terminal i get the following error message:

Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

I guess my new problem now is to get my desktop back and be able to browse my filesystem via Nautilus again...

---

### Post by aysiu on 2007-01-18
Whoa! How did that happen?

Can you try booting into recovery mode and then doing ```
mv /etc/fstab /etc/fstab.bad
/etc/fstab.backup /etc/fstab
reboot
```? Or is that what you already tried?

I don't see why removing this one line ```
/dev/sda1 /media/cdrom0 udf,iso9660 user,noauto 0 0
``` would create all those programs. Can anyone shed some light on this situation?

---

### Post by syalam on 2007-01-18
I actually did mv fstab.backup fstab

But either way it was just uncommenting a line right? Before I posted on the forums I uninstalled Beagle and some Beagle daemon and Synaptic might have removed Nautilus because it was linked somehow? Is there a way I can fix this?

I might just start everything from scratch again. Is there a way to reinstall Ubuntu from within Ubuntu? The way I installed it previously was making a bootable USB drive, but it was a hassle, and since i formatted my USB drive id have to do that all over again...

---

### Post by aysiu on 2007-01-18
One small thing you might want to try if you removed some stuff is just to put all the default packages back: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by syalam on 2007-01-18
That was a huge timesaver. Everything is back to normal! I appreciate all of your help. I guess we can move onto the next option for trying to read my USB drive? ha...

---

