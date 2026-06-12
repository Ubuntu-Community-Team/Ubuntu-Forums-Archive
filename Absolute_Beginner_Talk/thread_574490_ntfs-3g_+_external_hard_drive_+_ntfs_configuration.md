---
title: "ntfs-3g + external hard drive + ntfs configuration tool = unmountable?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by crash_x on 2007-10-12
Hi all,

I've been going through the forum reading through other people's similar questions and solutions, but none have so far worked for me.

I just switched from Windows XP to Ubuntu Feisty and I love it, but I cant seem to get my external ntfs media drive working.

At first, the drive would mount, but was read-only. I then used the ntfs configuration tool to enable read/write access to the drive which rendered it unmountable.

"mount -t ntfs-3g ... " forced or not does not work. For some reason ntfs-3g is not recognized as a valid file system. Also, the ntfs-3g command, used as an alternate, will not mount the drive.

The drive can be forcefully mounted as read-only using "pmount" , but if I use -t and specify ntfs-3g, the command fails specifying the ntfs-3g is not a valid filesystem.

Here is my fdisk -l output:
[INDENT]
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1045     8393931   83  Linux
/dev/hda2            1046        1176     1052257+  82  Linux swap / Solaris
/dev/hda3            1177        4865    29631892+  83  Linux

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS[/INDENT]

I have absolutely no idea what's going on. :confused: Can anyone help me out?

Thanks!

Regards,
Andrew

---

### Post by Beggar on 2007-10-12
It almost sounds like you dont have ntfs-3g installed, what are the results of 

```

sudo apt-get install ntfs-3g

```

---

### Post by lH)4~mK0e on 2007-10-12
If you open Adept from the System menu, you should be able to search for installs labeled "ntfs." Make sure all the ntfs3g libs and ntfstools are installed.   You may need to run something like

```
 sudo ntfsfix /dev/sdb(whatever number your usb filesystem is)
```

Then run:

```
sudo mkdir /media/ntfs 
sudo mount -t ntfs-3g /dev/sdb(whatever number your usb filesystem is) /media/ntfs
```

---

### Post by crash_x on 2007-10-13
Hi,

This is my terminal output:

[INDENT]crash-x@Pnet-mediahost:~$ sudo ntfsfix /dev/sda1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
NTFS partition /dev/sda1 was processed successfully.
crash-x@Pnet-mediahost:~$ sudo mount -t ntfs-3g /dev/sda1 /media/disk
Volume is scheduled for check. Please boot into Windows TWICE, or
use the 'force' mount option. For example type on the command line:

    mount -t ntfs-3g /dev/sda1 /media/disk -o force

Or add the option to the relevant row in the /etc/fstab file:

    /dev/sda1 /media/disk ntfs-3g defaults,force 0 0

crash-x@Pnet-mediahost:~$ sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force
WARNING: Dirty volume mount was forced by the 'force' mount option.[/INDENT]

The drive has now mounted successfully...

Will I have to perform these commands at each boot?

I really appreciate your help!!

Regards,
Andrew

---

### Post by vanadium on 2007-10-13
An external drive mounts automatically under ubuntu. However, Ubuntu won mount it if there is an error in the filesystem, unless you "force" the mount. In order to mount your disk automatically, you have to make sure the file system is all right. The output you provided already says how: you need to check the volume under Windows apparently to be able to remove the "dirty" bit, the bit telling that the system needs checking.

As a remark, unfortunately, when you use ntfs, you are still dependent on Windows. There seems to be no Linux approach to completely fix the disk. If you do not have windows, your only option is to mount using the -force option. I am a total ubuntu convert, yet I have a Lacie Silverscreen, which I formatted in ntfs so that I can load DVD images. If ever something happens to that file system, I will need to hunt for some kind soul having a Windows machine, unfortunately (yet there are still many of these around ;)

---

### Post by crash_x on 2007-10-13
Hi vanadium,

Thanks for your reply, it was very clear and informative. I took your suggestion, booted into windows with the drive using my work laptop, check the disk, properly unmounted it and reattached it to my home desktop. Voila, it works perfectly. Thanks!

Regards,
Andrew

---

### Post by crash_x on 2007-11-12
Fixed!! See here [http://ubuntuforums.org/showthread.php?t=168221&page=4](http://ubuntuforums.org/showthread.php?t=168221&page=4) and scroll down a bit

---

