---
title: "Windows Machine"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by GaryLittlemore on 2008-03-10
My XP machine has crashed and I've booted Ubuntu from the CD, In which folder can I find the windows files because I want to get stuff off the drive before I install Ubuntu?

Can anyone help me please?

---

### Post by elpichi on 2008-03-10
in the bar on top of the desktop click on 
Places > Computer
and at your left hand side you should be able to see the windows partition, for me is called sda1.
You'll recognize it when you see it as is the only drive with WINDOWS folder on it XD

---

### Post by GaryLittlemore on 2008-03-10
It says it can't mount SDA1, I've done 'sudo fdisk -l' and below is what was printed.

Could my drive be knackered?

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x149c149c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3737    30017421    7  HPFS/NTFS

---

### Post by forrestcupp on 2008-03-10
Have you tried booting to your XP CD and choosing the option to repair your OS instead of installing it?  That may get you to where you can at least boot to XP long enough to back up your files.

---

### Post by alphaniner on 2008-03-10
If XP crashed or wasn't shut down properly, you can't mount the drive.  There's another thread that's on that topic right now which you should check out:

[Can't mount Windows dev/sda2]("http://ubuntuforums.org/showthread.php?t=720646")

---

### Post by Duck2006 on 2008-03-10
They havn't said if they can still boot to windoze but yes i see if you can boot it or repair it and then move your files the load ubuntu as forrestcupp posted.

---

### Post by aysiu on 2008-03-10
Can you post the output of these commands? ```
sudo mkdir /media/recovery
sudo mount -t ntfs /dev/sda1 /media/recovery -o nls=utf8,umask=0222
cd /media/recovery
ls
``` (Please copy and paste instead of retyping)

---

### Post by GaryLittlemore on 2008-03-10
I've done what you have asked and this is what it said

ubuntu@ubuntu:~$ sudo mkdir /media/recovery
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /media/recovery -o nls=utf8,umask=0222
ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
Unmounting /dev/sda1 ()
ubuntu@ubuntu:~$ cd /media/recovery
ubuntu@ubuntu:/media/recovery$ ls

---

### Post by Shazaam on 2008-03-10
Will it boot into Safe Mode? F8 during a Windows boot will get you there. Run a chkdsk if it boots into Safe Mode..

---

### Post by GaryLittlemore on 2008-03-10
No it won't even boot in safe mode.

---

