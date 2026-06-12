---
title: "Ubuntu hates my external hard drive?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by hesavedave on 2008-01-02
I just got done installing Ubuntu and it won't recognize my external hard drive which I use for all my media. When I ran the Live CD it showed an icon on the desktop for my drive but now there is no icon. What can I do?:confused:

---

### Post by Rocket2DMn on 2008-01-02
I don't think it hates your drive.  Can you please plug in your drive and post the output of ```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by hesavedave on 2008-01-02
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d27700d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375        6436      498015   82  Linux swap / Solaris
/dev/sda3            6437       10011    28716187+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6485a634

---

### Post by Rocket2DMn on 2008-01-02
Can you also please post "cat /etc/fstab" and tell me if your external hard drive is formatted with NTFS?

---

### Post by bindatype on 2008-01-02
This is a common mistake--you won't see the external hard disk in fstab unless you put it there. This is what you must do: plug the drive in and (assuming it is a USB connection) check the following
```

$ sudo lsusb

```
and
```

$ sudo dmesg | tail

```

You are looking for something that looks like /dev/hdb1 of /dev/sdb1, etc...remember what you see b/c you will have to use it in a moment--I'll assume you found something that read /dev/sdb1.

Next, create a directory to mount the drive to--for example, we'll call it testdir

```

$ sudo mkdir /mnt/testdir

```

Many usb drives are formatted as vfat so that's the example I'll use

```

$ sudo mount -t vfat /dev/sdb1 /mnt/testdir

``` 

If for some reason it doesn't come up writable then do this
```

$ sudo mount -o remount,rw /mnt/testdir

```

---

### Post by Rocket2DMn on 2008-01-02
> **bindatype said:**
> This is a common mistake--you won't see the external hard disk in fstab unless you put it there.
Thank you.  It is true that externals aren't normally there unless you put them in, but if the drive was there when he installed or upgraded, it could be, that's why I asked for it.

If it IS in your /etc/fstab file, you will want to remove it - this will allow the drive to automount.
Most external hard drive that you buy these days are pre-formatted with NTFS.  If your drive is NTFS, you will have to install ntfs-3g in order to read/write to it.
```
sudo apt-get install ntfs-3g ntfs-config ntfsprogs
``` (those might be redundant due to package dependencies, but it's ok).  Then you can enable read/write by going to Applications->System Tools->NTFS Configuration Tool and checking the boxes for write support.

---

### Post by bindatype on 2008-01-02
I don't mean to be contradictory but if the drive is in fstab then he can set 'auto' in the third column _and_ remove 'noauto' from the fourth column and it should automatically mount on connection or when ```
$ sudo mount -a
``` is issued.

The 'auto' in third column means to auto-detect the filesystem type (can be very handy) and the 'noauto' in the fourth column means to do not auto mount.

As far as the NTFS thing goes, I was not aware of that--very interesting.

---

### Post by txHarleyMan on 2008-01-02
I kinda have the same problem.  I have an external USB drive I use for backup.  All formatted EXT3.  When I power it on it automounts to /media/disk-1/ and a folder opens and things work correctly.  But after 10 mins or so, the icon disappears from my desktop.  And it is gone from my file manager.  Like it unmounted itself on it's own.

Anyone have a thought on this?

Thank you.

Mike

---

### Post by Rocket2DMn on 2008-01-02
> **bindatype said:**
> I don't mean to be contradictory but if the drive is in fstab then he can set 'auto' in the third column _and_ remove 'noauto' from the fourth column and it should automatically mount on connection or when ```
$ sudo mount -a
``` is issued.

The 'auto' in third column means to auto-detect the filesystem type (can be very handy) and the 'noauto' in the fourth column means to do not auto mount.

As far as the NTFS thing goes, I was not aware of that--very interesting.

FYI, the auto/noauto in the 4th column is for when the computer is booting.  noauto means that it won't mount the drive even though it's listed,
I think if you want it to automount at a specific location in /media you need to delete the folder with the name (NOT WHILE ITS MOUNTED!), and use "ntfslabel" to give the drive the folder name you want.  Ex: I ntfslabel-ed my external to "usbdisk" so it mounts at /media/usbdisk when I plug it in.

> **txHarleyMan said:**
> I kinda have the same problem.  I have an external USB drive I use for backup.  All formatted EXT3.  When I power it on it automounts to /media/disk-1/ and a folder opens and things work correctly.  But after 10 mins or so, the icon disappears from my desktop.  And it is gone from my file manager.  Like it unmounted itself on it's own.

Anyone have a thought on this?

Thank you.

Mike

Are you using a drive like Seagate's FreeAgent drives?  These tend to put the disk into a sleep mode when not in use which will cause it to unmount,

---

### Post by txHarleyMan on 2008-01-02
> **Rocket2DMn said:**
> FYI, the auto/noauto in the 4th column is for when the computer is booting.  noauto means that it won't mount the drive even though it's listed, but should mount when you run "sudo mount -a".
I think if you want it to automount at a specific location in /media you need to delete the folder with the name (NOT WHILE ITS MOUNTED!), and use "ntfslabel" to give the drive the folder name you want.  Ex: I ntfslabel-ed my external to "usbdisk" so it mounts at /media/usbdisk when I plug it in.



Are you using a drive like Seagate's FreeAgent drives?  These tend to put the disk into a sleep mode when not in use which will cause it to unmount,

No, it's not a FreeAgent drive.  It just says Seagate on it.


mike@mike-desktop:~$ lsusb
Bus 005 Device 007: ID 0bc2:0502 Seagate RSS LLC

---

### Post by bindatype on 2008-01-02
I'm not sure that we aren't talking across purposes but here goes anyway: If you check the man pages you'll find this for noauto

" noauto Can only be mounted explicitly (i.e., the -a option will not cause the file system to be mounted)."

I don't see how that is consistent with what you wrote,> noauto means that it won't mount the drive even though it's listed, but should mount when you run "sudo mount -a".

I'm not trying to be provocative, just trying to be clear and accurate. If I am mistaken my apologies.

---

### Post by Rocket2DMn on 2008-01-02
You're not being provacative.  If the man page says mount -a won't load it, then it won't (I've never used the noauto feature) - I didn't check.  It still won't mount on boot :).  I'll fix my post.

txHarleyMan, I think you need to start a new thread for this, I don't have another answer for you, hopefully somebody else will.  Good luck.

Right now, let's wait for the OP to post back so we can make sure his problem is solved.

---

### Post by txHarleyMan on 2008-01-02
OK.  Sorry for the hijacking.

---

### Post by txHarleyMan on 2008-01-04
If it's any help - I traced my issue downto the FGLRX driver.  I uninstalled it and all is well.  Since then I tossed the ATI X600 and installed an NVIDIA 8600 GT.  Works great.

---

