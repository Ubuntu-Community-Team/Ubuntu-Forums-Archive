---
title: "Permissions Problems and My External Hard-Drive"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by blue_thunder on 2007-05-28
Hi all!

Just a few weeks ago I was able to read and write to my Maxtor external hard drive. Today I seem to have royally messed things up. Hopefully you guys can help. Here's some relevant outputs:

**for fdisk -l**
```
sthehi07@dhcp81:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7013    56331891   83  Linux
/dev/hda2            7014        7296     2273197+   5  Extended
/dev/hda5            7014        7296     2273166   82  Linux swap / Solaris

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12187    97892046    7  HPFS/NTFS
```

**/etc/fstab**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1     /media/SHAUNXHD1     ntfs-3g     defaults,locale=en_US.utf8   0    0


**some lines from dmesg**
```
[4294781.870000] Initializing USB Mass Storage driver...
[4294781.870000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294781.871000] usb-storage: device found at 3
[4294781.871000] usb-storage: waiting for device to settle before scanning
[4294781.871000] usbcore: registered new driver usb-storage
[4294781.871000] USB Mass Storage support registered.
[4294786.924000]   Vendor: Maxtor    Model: OneTouch II       Rev: 023g
[4294786.924000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4294786.930000] usb-storage: device scan complete
[4294787.043000] Driver 'sd' needs updating - please use bus_type methods
[4294787.097000] SCSI device sda: 195813072 512-byte hdwr sectors (100256 MB)
[4294787.097000] sda: assuming drive cache: write through
[4294787.191000] SCSI device sda: 195813072 512-byte hdwr sectors (100256 MB)
[4294787.191000] sda: assuming drive cache: write through
[4294787.191000]  sda: sda1
[4294787.214000] sd 0:0:0:0: Attached scsi disk sda
[4294787.239000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294977.578000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4294977.644000] NTFS volume version 3.1.
[4295544.992000] NTFS volume version 3.1.
[4295596.821000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295596.821000] NTFS-fs warning (device sda1): ntfs_filldir(): Skipping unrepresentable inode 0xd48.
[4295596.872000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295596.873000] NTFS-fs warning (device sda1): ntfs_filldir(): Skipping unrepresentable inode 0xd51.
[4295596.873000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295596.874000] NTFS-fs warning (device sda1): ntfs_filldir(): Skipping unrepresentable inode 0xd52.
[4295596.874000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295596.874000] NTFS-fs warning (device sda1): ntfs_filldir(): Skipping unrepresentable inode 0xd53.
[4295596.875000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295596.875000] NTFS-fs warning (device sda1): ntfs_filldir(): Skipping unrepresentable inode 0xd54.
[4295602.423000] printk: 16 messages suppressed.
[4295602.423000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295607.696000] printk: 11 messages suppressed.
[4295607.697000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295612.474000] printk: 3 messages suppressed.
[4295612.474000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295617.852000] printk: 21 messages suppressed.
[4295617.852000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295622.503000] printk: 31 messages suppressed.
[4295622.503000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295627.677000] printk: 1 messages suppressed.
[4295627.678000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295632.700000] printk: 1 messages suppressed.
[4295632.700000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295724.608000] NTFS volume version 3.1.
```

**after entering ls -la /media**
```
sthehi07@dhcp81:~$ sudo ls -la /media
total 24
drwxr-xr-x  6 root     root     4096 2007-05-28 12:29 .
drwxr-xr-x 24 root     root     4096 2007-01-06 00:52 ..
lrwxrwxrwx  1 root     root        6 2005-10-27 07:11 cdrom -> cdrom0
drwxr-xr-x  2 root     root     4096 2005-10-27 07:11 cdrom0
drwxr-xr-x  2 root     root     4096 2007-05-28 12:29 maxtor
drwxr-xr-x  2 sthehi07 sthehi07 4096 2006-08-19 11:26 SHAUNXHD1
drwxr-xr-x  2 root     root     4096 2006-08-19 09:53 usbdisk
```

see I forgot about "SHAUNXHD1" so today I made "maxtor"...anyway I can;t figure out how to make things right. I just need to be able to read and write to this thing.

One last thing

**results from mount -a**
```
sthehi07@dhcp81:~$ sudo mount -a
Couldn't mount device '/dev/sda1': Operation not supported
Windows did not shut down properly.  Try to mount volume in windows, shut down and try again.
Mount failed.

```

Thank you in advance for any advice you can give.

---

### Post by blue_thunder on 2007-05-28
Hi all!

Just a few weeks ago I was able to read and write to my Maxtor external hard drive. Today I seem to have royally messed things up. Hopefully you guys can help. Here's some relevant outputs:

**for fdisk -l**
```
sthehi07@dhcp81:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7013    56331891   83  Linux
/dev/hda2            7014        7296     2273197+   5  Extended
/dev/hda5            7014        7296     2273166   82  Linux swap / Solaris

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12187    97892046    7  HPFS/NTFS
```

**/etc/fstab**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1     /media/SHAUNXHD1     ntfs-3g     defaults,locale=en_US.utf8   0    0


**some lines from dmesg**
```
[4294781.870000] Initializing USB Mass Storage driver...
[4294781.870000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294781.871000] usb-storage: device found at 3
[4294781.871000] usb-storage: waiting for device to settle before scanning
[4294781.871000] usbcore: registered new driver usb-storage
[4294781.871000] USB Mass Storage support registered.
[4294786.924000]   Vendor: Maxtor    Model: OneTouch II       Rev: 023g
[4294786.924000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4294786.930000] usb-storage: device scan complete
[4294787.043000] Driver 'sd' needs updating - please use bus_type methods
[4294787.097000] SCSI device sda: 195813072 512-byte hdwr sectors (100256 MB)
[4294787.097000] sda: assuming drive cache: write through
[4294787.191000] SCSI device sda: 195813072 512-byte hdwr sectors (100256 MB)
[4294787.191000] sda: assuming drive cache: write through
[4294787.191000]  sda: sda1
[4294787.214000] sd 0:0:0:0: Attached scsi disk sda
[4294787.239000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294977.578000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4294977.644000] NTFS volume version 3.1.
[4295544.992000] NTFS volume version 3.1.
[4295596.821000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295596.821000] NTFS-fs warning (device sda1): ntfs_filldir(): Skipping unrepresentable inode 0xd48.
[4295596.872000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295596.873000] NTFS-fs warning (device sda1): ntfs_filldir(): Skipping unrepresentable inode 0xd51.
[4295596.873000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295596.874000] NTFS-fs warning (device sda1): ntfs_filldir(): Skipping unrepresentable inode 0xd52.
[4295596.874000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295596.874000] NTFS-fs warning (device sda1): ntfs_filldir(): Skipping unrepresentable inode 0xd53.
[4295596.875000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295596.875000] NTFS-fs warning (device sda1): ntfs_filldir(): Skipping unrepresentable inode 0xd54.
[4295602.423000] printk: 16 messages suppressed.
[4295602.423000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295607.696000] printk: 11 messages suppressed.
[4295607.697000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295612.474000] printk: 3 messages suppressed.
[4295612.474000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295617.852000] printk: 21 messages suppressed.
[4295617.852000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295622.503000] printk: 31 messages suppressed.
[4295622.503000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295627.677000] printk: 1 messages suppressed.
[4295627.678000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295632.700000] printk: 1 messages suppressed.
[4295632.700000] NTFS-fs error (device sda1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.  You might want to try to use the mount option nls=utf8.
[4295724.608000] NTFS volume version 3.1.
```

**after entering ls -la /media**
```
sthehi07@dhcp81:~$ sudo ls -la /media
total 24
drwxr-xr-x  6 root     root     4096 2007-05-28 12:29 .
drwxr-xr-x 24 root     root     4096 2007-01-06 00:52 ..
lrwxrwxrwx  1 root     root        6 2005-10-27 07:11 cdrom -> cdrom0
drwxr-xr-x  2 root     root     4096 2005-10-27 07:11 cdrom0
drwxr-xr-x  2 root     root     4096 2007-05-28 12:29 maxtor
drwxr-xr-x  2 sthehi07 sthehi07 4096 2006-08-19 11:26 SHAUNXHD1
drwxr-xr-x  2 root     root     4096 2006-08-19 09:53 usbdisk
```

see I forgot about "SHAUNXHD1" so today I made "maxtor"...anyway I can;t figure out how to make things right. I just need to be able to read and write to this thing.

One last thing

**results from mount -a**
```
sthehi07@dhcp81:~$ sudo mount -a
Couldn't mount device '/dev/sda1': Operation not supported
Windows did not shut down properly.  Try to mount volume in windows, shut down and try again.
Mount failed.

```

Thank you in advance for any advice you can give.

---

### Post by blue_thunder on 2007-05-28
Any ideas?

---

### Post by chager on 2007-05-28
Delete the NTSF-3g drivers

---

### Post by blue_thunder on 2007-05-28
Admittedly noobish question: how do I do that?

---

### Post by chager on 2007-05-28
If you installed the NTFS-3g drivers, the first thing I would do is uninstall that driver.  I'm a newbie so all I can do is suggest . . .

---

### Post by chager on 2007-05-28
OK, first did you install the NTFS-3g driver?

---

### Post by blue_thunder on 2007-05-28
I did, but a while ago. And I'm using Dapper by the way. Also, the way I did it was probably just following the steps on a forum.

---

### Post by chager on 2007-05-28
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Here is the link . . .  

If you need to read NTFS files, I would leave the driver.  I think you need to unmount and remount the drive, and then reboot.  The link above explains how.

---

### Post by chager on 2007-05-28
I would post this problem on the 217009 thread . . .

---

### Post by notquitemichael on 2007-05-28
a few pointers, just incase you haven't tried it;

you need to plug your machine into a windows computer, and then safely eject it so that windows can close the filesystem safely (which would appear to be the chief problem.)

secondly, replace "defaults" in the fstab with:
nls=utf8

thirdly, if you can't access it, do:

gksudo nautilus and attempt to access it from there

NOTE becareful what you do, because you're going around your hardrives as the root user which is never a good idea.

should you be able to you need to go to /media or /mount depending on where your access folders are, right click on the folder with the same name as the drive (i think it was maxtor?) then choose properties, permissions and in owner choose your login name, and choose read and write.

then save, and close the window and try it from a normal instance of nautilius.

should work.

have fun. - tom.

---

### Post by sistarbliss on 2007-05-28
I also need help with writing to an external hard drive.  I have a new install of Ubuntu and am a noob.  How do I set permissions to write to it?  I can read from it just fine.

---

### Post by (chubbstar) on 2007-05-29
i also lost access to my external hard drive after the kernel update. why is this happening to us and why has no one figured out a solution?

---

### Post by pinknyunyu on 2007-05-30
I'm completely new to Linux, using Feisty, and my external hard drive is now read-only...I logged in as root, and tried to change the permission that way, but it would not let me change it, and now I can't do anything.

Don't want to go back to Windows.

---

### Post by FXFman1209 on 2007-05-30
I had the exact same problem. If you seem to only be able to read from your external harddrive, then the filesystem on it is probably NTFS. You need to install something to write to it.

1) Go to **Applications**->**Add/Remove**
2) Search for 'ntfs'
3) You should see "NTFS Configuration Tool"
4) Install it
5) After it's installed, **Applications**->**System Tools**->**NTFS Configuration Tool**

You should be able to easily figure out the rest. Enjoy!

---

