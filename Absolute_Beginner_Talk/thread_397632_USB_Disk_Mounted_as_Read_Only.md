---
title: "USB Disk Mounted as Read Only"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by doctorj on 2007-03-30
I have read other threads about USB hard drives being mounted as read only. I cannot see anywhere that tells me how to change the permission to "rw"?

What can I do to simply make the drive mounted as rw?

:(

---

### Post by taurus on 2007-03-30
What filesystem is your USB harddrive?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by doctorj on 2007-03-30
Output:

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6997    56203371   83  Linux
/dev/hda2            6998        7297     2409750    5  Extended
/dev/hda5            6998        7297     2409718+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    7  HPFS/NTFS

---

### Post by doctorj on 2007-03-30
I missed a bit of that output:

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6997    56203371   83  Linux
/dev/hda2            6998        7297     2409750    5  Extended
/dev/hda5            6998        7297     2409718+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    7  HPFS/NTFS

:(

---

### Post by K.Mandla on 2007-03-30
Are you mounting it with *sudo mount* or is it automounting somehow?

---

### Post by doctorj on 2007-03-30
I am not mounting it manually. It is ready and showing on my desktop after arriving at my desktop from a boot. It is mounted automatically.

---

### Post by taurus on 2007-03-30
Try

```
sudo umount /dev/sda1
sudo mount -t ntfs /dev/sda1 /media/usbdrive -o nls=utf8,umask=0222
ls -la /media/usbdrive
```

---

### Post by doctorj on 2007-03-30
After inputting the second line you have given me it replies:

```
sudo mount -t ntfs /dev/sda1 /media/usbdrive -o nls=utf8,umask=0222
```

```
mount: mount point /media/usbdrive does not exist
```

:(

---

### Post by martinw89 on 2007-03-30
That just means the folder does not exist (I know, why couldn't it just say that?:) )  To make the folder you can use Nautilus (the file browser, go to Places -> Computer) or you can type ```
sudo mkdir /media/usbdrive
```

---

### Post by doctorj on 2007-03-30
SO I was able to input those three lines, and on the last one it gives me the reply:

```
elwyn@elwyn-desktop:~$ ls -la /media/usbdrive
total 64
dr-xr-xr-x 1 root root  4096 2007-03-28 16:39 .
drwxr-xr-x 6 root root  4096 2007-03-31 12:58 ..
dr-xr-xr-x 1 root root  4096 2007-03-10 13:08 BUSINESS DOCUMENTS
dr-xr-xr-x 1 root root     0 2007-01-31 15:10 $INPLACE.~TR
dr-xr-xr-x 1 root root  4096 2006-12-29 09:59 MOVIES
dr-xr-xr-x 1 root root 16384 2007-02-28 17:12 MUSIC
dr-xr-xr-x 1 root root 16384 2007-01-30 16:35 OLD COMPUTER
dr-xr-xr-x 1 root root  4096 2007-02-21 09:09 PHOTOGRAPHS
dr-xr-xr-x 1 root root     0 2007-01-30 23:34 $RECYCLE.BIN
dr-xr-xr-x 1 root root 12288 2007-03-28 16:39 System Volume Information
```

But when I go to use the drive again it still gives me "Error while moving items to "/media/usb...PHS/FAMILY". You do not have permissions to write to this folder.'

:(

---

### Post by taurus on 2007-03-30
You cannot write to ntfs with ntfs driver.  You need to install ntfs-3g if you want to write to it.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

