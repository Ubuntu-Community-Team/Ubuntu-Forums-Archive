---
title: "Hard Drive Accessing Help"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Dariusgaiden on 2007-03-09
Hey all! Im new to the Ubuntu OS, so far I love it, however I was wondering this, I have a 2nd hard drive in my comp that has all of my files, mp3s movies, etc, how can I access this? It says it must be mounted and I am unable to do so, it is a NTFS file system. Thanks for the help

---

### Post by kelbizzle on 2007-03-09
ok then this is what you do. 
```
sudo fdisk -l
```
To find out where the ntfs volume is located.  Under the system column you'll see it says ntfs.
The device location will look something like this. "/dev/hda1"

If you want to mount that partiton once in a while, whenever you need it. Do this.. In terminal
**to mount the partition**
```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

```

**To unmount it **
```
sudo umount /media/windows/

```

**If you want to mount it automatically at boot...do this **
```
sudo mkdir /media/windows
```
```
sudo cp /etc/fstab /etc/fstab_backup
```
```
gksudo gedit /etc/fstab
```

Add this line to the end of your fstab
```
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
```

and then finally remount your fstab
```
sudo mount -a
```

---

### Post by Dariusgaiden on 2007-03-09
Great thanks for the hlp, I think it worked but it says I do not have permission to access files?

---

### Post by kelbizzle on 2007-03-10
with method did you use?

---

### Post by Dariusgaiden on 2007-03-10
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

do you write this as one code? or each one line separtely?
Drive information
Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241    7  HPFS/NTFS

---

### Post by Dariusgaiden on 2007-03-10
Nevermind got it to work thanks!

---

### Post by dhughes on 2007-03-10
> **Dariusgaiden said:**
> 

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab



 Each line separately.

---

### Post by Dariusgaiden on 2007-03-11
Ok I am having a problem mounting the hard drive on boot here is what i entered
mkdir: cannot create directory `/media/windows': File exists
darius@darius-desktop:~$ sudo cp /etc/fstab /etc/fstab_backup
darius@darius-desktop:~$ gksudo gedit /etc/fstab/dev/hdb1    /media/windows ntfs  nls=utf8,umask=0222 0    0

(gedit:6546): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (gedit:6546): WARNING **: Hit unhandled case 19 (Not a directory) in gedit_unrecoverable_loading_error_message_area_new.

Any ideas?

---

### Post by SouthernGorilla on 2007-03-12
Would changing this line ```
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
``` to this ```
/dev/hda1    /media/windows ext3  nls=utf8,umask=0222 0    0
``` work for an ext3 partition?
Currently my fstab reads ```
/dev/sdb1 /usr0 ext3 defaults 0 0
``` and the drive does not mount at boot. I noticed a message during boot recently > [17179832.700000] ext3: No journal on filesystem on sdb1 What does that indicate?

---

