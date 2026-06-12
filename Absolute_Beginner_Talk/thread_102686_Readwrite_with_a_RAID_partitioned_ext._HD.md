---
title: "Read/write with a RAID partitioned ext. HD"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by qiemem on 2005-12-12
Hate to repost, but I'd really like to get this working and I figured the somewhat high reply number might be scaring people away. Here's the problem:

Just switched to Linux from WinXP. I have an external harddrive (Western Digital 120gb USB 2.0 if it matters) on which I backup files, keep my music, etc. Anyway, it mounts fine, automatically and everything, and I can read off it (hell, I'm listening to music off it right now), but I can't seem to write to it at all. Its listed as having 0 free space left. I've looked around for how to fix this, but everything I find either doesn't apply to me (assumes new hard drive, etc) or goes way over my head. What should I do? Obviously, I'd like to keep all my old data.

Info:
```

$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 6996 56195338+ 83 Linux
/dev/sda2 6997 7296 2409750 5 Extended
/dev/sda5 6997 7296 2409718+ 82 Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdc1 1 14593 117218241 fd Linux raid autodetect

$ mount

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=bryan)
/dev/sdc1 on /media/WD USB 2 type vfat (rw,nosuid,nodev,quiet,shortname=winnt,uid=1000,gi d=1000,umask=077,iocharset=utf8)

$ cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sdb /media/usb0 auto rw,user,noauto 0 0

```
Any ideas? Or any ideas about where to look/where to ask?

---

### Post by NotJustANewbie on 2005-12-12
Ok, back up all of your data to DVD or internal HD or whatever.

Then format the external hardisk with ReiserFS or ext3.  It should work.  I had the same problem with my iPod, being I could read and listen to music form it, but not write to it.  Hope this solves your problem.

EDIT: You have to change the permissions of the external hard drive. I just remembered. Google will help you.

Good luck!

---

### Post by qiemem on 2005-12-12
Damn, I was afraid of that...
But the filesystem is vfat... you sure I have to repartition it? I thought I only had to do that for NTFS...
Oh well... if no one has anymore ideas, I'll give that a shot...

Thanks for the post!

---

### Post by psusi on 2005-12-12
You do NOT want to format it for ext3 or reiserfs unless you don't mind not being able to use it in a windows machine.  

I am a little confused as to why the partition tag says it is a linux raid partition when it obviously is not.  You may be getting the error because the filesystem is corrupted so the driver is mounting it as read only.  Check the output of dmesg and /var/log/messages for any errors.  

You also might try to unmount it and fsck it:

sudo umount /dev/sdc1
sudo fsck.vfat /dev/sdc1


[QUOTE=qiemem]Damn, I was afraid of that...
But the filesystem is vfat... you sure I have to repartition it? I thought I only had to do that for NTFS...
Oh well... if no one has anymore ideas, I'll give that a shot...

Thanks for the post![/QUOTE]

---

### Post by qiemem on 2005-12-12
Don't exactly know what I'm looking for, but heres what I think is the relevent part of dmesg
```
[4294679.264000] Initializing USB Mass Storage driver...
[4294679.265000] scsi2 : SCSI emulation for USB Mass Storage devices
[4294679.265000] usb-storage: device found at 3
[4294679.265000] usb-storage: waiting for device to settle before scanning
[4294679.265000] usbcore: registered new driver usb-storage
[4294679.265000] USB Mass Storage support registered.
[4294679.612000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[4294679.612000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294679.615000] ACPI: Thermal Zone [THM] (28 C)
[4294679.829000] Attempting manual resume
[4294679.830000] swsusp: Suspend partition has wrong signature?
[4294679.845000] kjournald starting.  Commit interval 5 seconds
[4294679.845000] EXT3-fs: mounted filesystem with ordered data mode.
[4294680.886000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294683.398000] Adding 2409708k swap on /dev/sda5.  Priority:-1 extents:1
[4294683.714000] EXT3 FS on sda1, internal journal
[4294684.270000]   Vendor: WD        Model: 1200BB External   Rev: 0412
[4294684.270000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294684.271000] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
[4294684.271000] sdb: assuming drive cache: write through
[4294684.272000] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
[4294684.272000] sdb: assuming drive cache: write through
[4294684.272000]  /dev/scsi/host2/bus0/target0/lun0: p1
[4294684.287000] Attached scsi disk sdb at scsi2, channel 0, id 0, lun 0
[4294684.287000] usb-storage: device scan complete

```

I didn't notice any errors with dmesg or cat /var/log/messages.

And then when I tried to fsck it:
```
$ sudo fsck.vfat /dev/sdb1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  67:c8/47, 68:73/3e, 69:ae/09, 70:fb/14
1) Copy original to backup
2) Copy backup to original
3) No action
?

```
I don't know what this is, so I just quit and remounted the hd.

And yes, I definitly would like to have it be able to move back and forth between a windows machine and a linux machine.

Thanks for the help! But I this is going over my head a bit... What should I do from here?

---

### Post by psusi on 2005-12-13
The log you posted looks all normal, but doesn't appear to have anything to do with the drive in question.  If you unmount and remount the drive, then look at the last few lines that dmesg spits out, does that mention any errors?

Also try answering "No Action" to fsck and see if it finds any other errors.

---

### Post by qiemem on 2005-12-13
> Also try answering "No Action" to fsck and see if it finds any other errors.
Nope, no errors, just reported size and number of files.

> If you unmount and remount the drive, then look at the last few lines that dmesg spits out, does that mention any errors?

Nope, nothing... 
Though, the first line of the dmesg seemed kinda strange:
```
usp: Suspend partition has wrong signature?

```
Don't know if it has anything to do with this though.

---

### Post by psusi on 2005-12-13
That's just the kernel saying that it checked your swap partition to see if it had hibernation data saved on it and it didn't ( because you aren't resuming from hibernation ).  

Look at the last few lines of dmesg after you unmount and remount the partition.  

Also try this:

From the command line, cd to /media/WD USB 2

Once there, do this and post the results:

pwd
sudo echo foo > bar
ls -l bar

If that works ( i.e. the file bar gets created ) then the kernel can write to the filesystem just fine, it's just a permission problem ( you don't have access ).  The umask value in your fstab looks wrong to me, I think it should be 777 not 077.  If the above commands work, change the umask value from 077 to 777.  

[QUOTE=qiemem]Nope, no errors, just reported size and number of files.


Nope, nothing... 
Though, the first line of the dmesg seemed kinda strange:
```
usp: Suspend partition has wrong signature?

```
Don't know if it has anything to do with this though.[/QUOTE]

---

### Post by qiemem on 2005-12-13
```
$ cd /media/'WD USB 2'
/media/WD USB 2$ pwd
/media/WD USB 2
/media/WD USB 2$ sudo echo foo > bar
Password:
echo: write error: No space left on device
bryan@BryanH:/media/WD USB 2$ ls -l bar
-rwx------  1 bryan bryan 0 2005-12-13 12:48 bar

```
So it made the file but didn't write anything to it... no, I'm not just being dumb about space. It says it has 0 bytes left... What would cause it to not recognize the free space?

I tried dmesg again, looked at the last few lines... There about my ethernet connection... except for the last line:
```
[4312786.606000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```
But this wouldn't have anything to do with what we're talking about, would it?

Wait a sec... okay, so just to be sure I wasn't being a moron, I checked to how much space it thought was being used up... about 110gb... Well that's dangerously close to 120 I thought (but still thought it might see space as being used, I don't know...), then it hit me. I deleted a file, and guess freaking what? I'm really sorry for wasting everyone's time... I just couldn't believe that I had used every single last byte, but I guess I did when I was backing up all my old stuff (as much of it as possible). So yeah. I feel really bad now. But I guess there is a lesson to be learned here. I guess...

---

