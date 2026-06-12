---
title: "S Video &amp; External HD problems"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by azizzle on 2007-06-01
Ok, noob here, so please help out! These problems aren't related, i just figured i'd consolidate threads. I did try and search, before starting this, so please don't flame. My first problem is with my Svideo, everything is fine during startup until the login screen comes up. Then my tv goes blank. I'm using an Nvidia geforce 7900. Whats the deal here?

Second problem; I'm trying to copy some files to an external hard drive but it says i don't have permission to write to the folder. I right-clicked, properties, permission, but i can't change anything. Please help! Thanks

---

### Post by drowner on 2007-06-01
> **azizzle said:**
> Ok, noob here, so please help out! These problems aren't related, i just figured i'd consolidate threads. I did try and search, before starting this, so please don't flame. My first problem is with my Svideo, everything is fine during startup until the login screen comes up. Then my tv goes blank. I'm using an Nvidia geforce 7900. Whats the deal here?

Second problem; I'm trying to copy some files to an external hard drive but it says i don't have permission to write to the folder. I right-clicked, properties, permission, but i can't change anything. Please help! Thanks

I may be able to help with the second problem.

How is it formatted?

post the output of the command:
```

sudo fdisk -l
```

---

### Post by taurus on 2007-06-01
What filesystem is that external harddrive?  Post the output of this command here?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by drowner on 2007-06-01
Woot! I beat taurus!

And he said the same thing, EXACTLY, as me!

I'm becoming uber-elite ;)

---

### Post by taurus on 2007-06-01
> **drowner said:**
> Woot! I beat taurus!

And he said the same thing, EXACTLY, as me!

I'm becoming uber-elite ;)

](*,) #-o ](*,)

---

### Post by azizzle on 2007-06-01
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38156   306488038+  83  Linux
/dev/sda2           38157       38913     6080602+   5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7475    60042906    7  HPFS/NTFS

---

### Post by taurus on 2007-06-01
> **azizzle said:**
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38156   306488038+  83  Linux
/dev/sda2           38157       38913     6080602+   5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
**[COLOR="Blue"]/dev/sdb1               1        7475    60042906    7  HPFS/NTFS[/COLOR]**

Since it's ntfs filesystem, you need to install ntfs-3g (and ntfs-config) if you want to write to it.  If you are running feisty, just do

```
sudo aptitude update
sudo aptitude install ntfs-3g 
sudo mkdir /media/sdb1
sudo umount /dev/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media
```

---

### Post by azizzle on 2007-06-01
Ok, i did that, but it still says i dont have permission. I am running feisty too

---

### Post by Inxsible on 2007-06-01
```
sudo chown -R <your-username>:<your group>  <device-name>
```

---

### Post by azizzle on 2007-06-01
did sudo chown -R andrew /media/disk
still can't write to it! Thanks for the help so far. I really appreciate it.

---

### Post by azizzle on 2007-06-01
wait what is my group? how do i find that out?

---

### Post by Inxsible on 2007-06-01
most time it is the same as your username, unless you have changed it specifically

---

### Post by azizzle on 2007-06-01
still don't have permission...

---

### Post by drowner on 2007-06-01
Can we check your fstab please?

cat /etc/fstab

---

### Post by azizzle on 2007-06-02
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ea123ca2-47b2-4548-8fef-abc937f7ed5e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3812cef0-f05c-419a-85d7-5e694c23c13e none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by taurus on 2007-06-02
Can you post

```
ls -la /media
```

---

### Post by azizzle on 2007-06-02
total 160
drwxr-xr-x  7 root root   4096 2007-06-01 22:22 .
drwxr-xr-x 21 root root   4096 2007-05-30 18:25 ..
lrwxrwxrwx  1 root root      6 2007-05-25 23:45 cdrom -> cdrom0
drwxr-xr-x  2 root root   4096 2007-05-25 23:45 cdrom0
dr-xr-xr-x  1 root root 135168 2007-05-30 23:01 disk
drwx------  2 root root   4096 2007-06-01 21:41 disk-1
lrwxrwxrwx  1 root root      7 2007-05-25 23:45 floppy -> floppy0
drwxr-xr-x  2 root root   4096 2007-05-25 23:45 floppy0
-rw-r--r--  1 root root    150 2007-06-01 22:22 .hal-mtab
--wxr-x---  1 root root      0 2007-04-15 04:56 .hal-mtab-lock
drwxr-xr-x  2 root root   4096 2007-06-01 20:03 sdb1

---

### Post by taurus on 2007-06-02
Can you try to run these three commands from a terminal again?

```
sudo umount /dev/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media
```
Post the output of the last command here.

---

### Post by azizzle on 2007-06-02
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
andrew@andrew-desktop:~$ ls -la /media
total 28
drwxr-xr-x  6 root root 4096 2007-06-01 22:52 .
drwxr-xr-x 21 root root 4096 2007-05-30 18:25 ..
lrwxrwxrwx  1 root root    6 2007-05-25 23:45 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-05-25 23:45 cdrom0
drwx------  2 root root 4096 2007-06-01 21:41 disk-1
lrwxrwxrwx  1 root root    7 2007-05-25 23:45 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-05-25 23:45 floppy0
-rw-r--r--  1 root root   76 2007-06-01 22:52 .hal-mtab
--wxr-x---  1 root root    0 2007-04-15 04:56 .hal-mtab-lock
drwxr-xr-x  2 root root 4096 2007-06-01 20:03 sdb1

---

### Post by taurus on 2007-06-02
Did you connect that external harddrive to a Windows machine before?  Sounds like you need to connect it back to a XP and unmount it cleanly before you can mount and write to it in Feisty.

---

### Post by azizzle on 2007-06-02
oh that's it. how do i unmount it from zp?

---

### Post by drowner on 2007-06-02
I think you can right click on it and select 'Eject', or if its usb click the little thing for 'safely remove device' in the notification area.

I dont use windows, so i dont know ;)

---

### Post by azizzle on 2007-06-02
ah ha! got it! thank you all so much! i see how it works now. thanks a lot!

---

