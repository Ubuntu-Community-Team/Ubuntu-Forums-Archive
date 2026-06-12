---
title: "usb hard drive wont mount"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by bigmahlman on 2007-12-14
My western digital pasport will not mount

ubuntu sees it just wont mount it

i get this error when i click on it 
Invalid mount option when attempting to mount the volume 'PHD'.
i would like to set it up for it auto mounts when i plug it in

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    c  W95 FAT32 (LBA)

i dont know if this will help anyone out.  When i searched around the forums other people posted it.

any help would be nice.  thank you

---

### Post by taurus on 2007-12-14
What happens if you try to mount it by hand from a terminal?

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by bigmahlman on 2007-12-14
my usb hard drive is now mounted

how do i get it to auto mount

---

### Post by bigmahlman on 2007-12-14
anyone got any ideas.   i have been searching around and cant find anything that is working for me

---

### Post by Rocket2DMn on 2007-12-14
To have it automount when you plug it in, you have to make sure there is no entry for it in /etc/fstab
Can you post the output of
```
cat /etc/fstab
sudo fdisk -l
```
while the drive is plugged in?
And are you sure it's FAT32 and not NTFS?

---

### Post by bigmahlman on 2007-12-14
yes it is fat32

why would it mount just fine with the command line, but not be able to auto mount?


andrew@andrews-notebook:~$ cat /etc/fstab

# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# /dev/sda2

UUID=9ccd09af-1de0-41a1-9427-f68736ed4a4f /               ext2    defaults,errors=remount-ro 0       1

# /dev/sda1

UUID=BA444D2E444CEF27 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

# /dev/sda3

UUID=17361d49-2507-49f4-b7b6-17015a648353 none            swap    sw              0       0

/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0


andrew@andrews-notebook:~$ sudo fdisk -l



Disk /dev/sda: 60.0 GB, 60011642880 bytes

255 heads, 63 sectors/track, 7296 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x8f1c38f1



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        6272    50376798+   7  HPFS/NTFS

/dev/sda2            6272        7164     7166976   83  Linux

/dev/sda3            7165        7295     1052257+  82  Linux swap / Solaris

/dev/sda4            7296        7296        6144   af  Unknown



Disk /dev/sdb: 120.0 GB, 120034123776 bytes

255 heads, 63 sectors/track, 14593 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x44fdfe06



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1       14593   117218241    c  W95 FAT32 (LBA)

---

### Post by ibbill on 2007-12-14
this is what I had to do to get my to mount  on restart of computer.

[http://ubuntuforums.org/showthread.php?t=584175](http://ubuntuforums.org/showthread.php?t=584175)

also I have to right click the drive an choose unmount before I reboot.

---

### Post by Rocket2DMn on 2007-12-14
In your /etc/fstab file you have 
> /dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
I'm not sure why that is there, perhaps it's typed in incorrectly b/c you might actually have 2 cd/dvd drives.  If that is the case you need to fix that to be correct.  Otherwise, comment out that line by putting a # at the front.
Once you have the line with /dev/sdb1 commented, your drive should automount (you MIGHT have to restart the computer, I'm not sure).

You can edit the fstab file using
```
gksudo gedit /etc/fstab
```

---

### Post by bigmahlman on 2007-12-14
i need that to be a little more noobish

and im using a laptop and the dvd drive mounts as usb i think.

---

### Post by Rocket2DMn on 2007-12-14
Hehe ok.  Please unplug your external drive.

Here's what your fstab file SHOULD look like.  I will disable (comment out) the line that has sdb1 set to mount at /media/cdrom0 since this is most likely not what you want.
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# /dev/sda2
UUID=9ccd09af-1de0-41a1-9427-f68736ed4a4f / ext2 defaults,errors=remount-ro 0 1
# /dev/sda1
UUID=BA444D2E444CEF27 /media/sda1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda3
UUID=17361d49-2507-49f4-b7b6-17015a648353 none swap sw 0 0

# this line appears to be incorrect
# sdb1 should be an external hard drive partition
# /dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0

I put a # in front of the sdb1 line, this means that the mounting program will ignore this line.  You should make a backup of your old fstab then replace fstab with the above configuration.  Here are 2 commands, the first will make a backup of fstab, the second will open up the fstab file where you can delete everything and copy and paste in what I just posted, save, and exit.

```
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```

Now try plugging in your hard drive.  If nothing happens, unplug it and reboot the computer.  Then try plugging in the hard drive.

---

### Post by bigmahlman on 2007-12-14
its all working fine now.

thank you so much.  

now i can finish getting my brothers new Christmas present finished.

ubuntu ftw!

---

