---
title: "Cannot mount shared HD in 7.04"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Mycle on 2007-09-26
Hi, I recentl upgraded my Ubuntu/WinXP dual boot computer to Feisty 7.04.
Now, when I go to the Places menu I see my 2 NTFS drives listed (and accessible) but my FAT32 shared drive is no listed. 

When I go to Places>Home Folder, or Places>Computer where the FAT32 shared drive *is* listed along with the others, while the NTFS drives are once again accessible, the FAT32 drive icon,  when clicked on, produces the error: "Cannot Mount Volume...Not privileged to mount the volume "LShare".
Can anyone please advise me on this?
Regards,
Mycle

---

### Post by rennen01 on 2007-09-26
Please paste output of

```
sudo mount
```

---

### Post by Mycle on 2007-09-27
Thanks for the reply. "sudo mount" produces the required info I believe but when I copy & past it to a text editor and try to save it anywhere, I'm unsuccessful. There seems to be other problems going on here. I could copy the list  by hand but that's complicating an already tricky situation. I did want to learn Ubuntu by solving problems that arose within a functioning OS  but it looks like I'm going to have to back-track and do some serious reading.

Regards,
Mycle

---

### Post by Mycle on 2007-09-27
I did some reading and things suddenly improved. No discernable connection between the two.
Here's the info produced from "sudo mount".

/dev/hda8 on / type ext3 (rw,errors=remount-ro) 
proc on /proc type proc (rw,noexec,nosuid,nodev) 
/sys on /sys type sysfs (rw,noexec,nosuid,nodev) 
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755) 
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777) 
procbususb on /proc/bus/usb type usbfs (rw) 
udev on /dev type tmpfs (rw,mode=0755) 
devshm on /dev/shm type tmpfs (rw) 
devpts on /dev/pts type devpts (rw,gid=5,mode=620) 
lrm on /lib/modules/2.6.17-10-386/volatile type tmpfs (rw) 
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw) 


Regards,
Mycle

---

### Post by Mycle on 2007-09-27
I've managed to fix it. In the /etc/fstab file the problem  /dev/hda9 line was commented out with the explanation: "Converted during the upgrade to Edgy" I just uncommented it and added som basic parameters I found in an Ubuntu User Guide. So it's either onward through a life of trouble free linux, or on to the next problem, whichever comes sooner.:)

Regards,
Mycle

---

### Post by rennen01 on 2007-09-27
Sorry got busy, I'm glad you got it fixed.

---

### Post by cajunlibra on 2007-10-11
> **Mycle said:**
> I've managed to fix it. In the /etc/fstab file the problem  /dev/hda9 line was commented out with the explanation: "Converted during the upgrade to Edgy" I just uncommented it and added som basic parameters I found in an Ubuntu User Guide. So it's either onward through a life of trouble free linux, or on to the next problem, whichever comes sooner.:)

Regards,
Mycle

What basic parameters did you use?  I'm having the same exact problem.
Here's my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4 -- converted during upgrade to edgy
UUID=a3ae2bd5-310a-4124-9d7a-626049eebc65 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=07D6-0316 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2 -- converted during upgrade to edgy
UUID=CC58102058100C38 /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=B833-06C0 /home/cajun/shared vfat users,owner,rw,umask=000 0 0
/dev/sdb1       /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0



sda2 is the XP partition
sda4 is Kubuntu
sda3 is my shared drive that should be accessible from Kubuntu and Xp


Thanks


mount prints:
root@cajunlibra:/# mount
/dev/sda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-386/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

### Post by cajunlibra on 2007-10-14
bump

---

### Post by vanadium on 2007-10-14
Only your system drive, sda4, is currently mounted. None of the other drives in fstab, sda1, sda2 and sda3, are mounted, even though they are listed in /etc/fstab. Look at the output of the command "sudo mount -a" and post the output here. It should print error messages for the drives that are listed, but not mounted.

The error might be due to a problem with the UUIDS mentionned. The easy way to fix that issue would be to replace the UUID= for the drives sda1, 2 and 3 by their device name, e.g. /dev/sda1 for sda1. To be safe, use comment marks to "delete" a line, e.g. like

# /dev/sda1 -- converted during upgrade to edgy
#UUID=07D6-0316 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/sda1 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1

I copied the line containing UUID, commented it out and edited the copy. This way, you can easily "revert".

The more correct solution would be to continue using the UUID= format, but then you need to check the UUIDS. I am not sure if blkid will give UUIDS for not mounted volumes, but what should work for sure, even on non mounted volumes, is for example

sudo vol_id /dev/sda1

Then check whether the UUID corresponds with that in /etc/fstab.

Another possibility occurs to me, and I am afraid that that in fact might be the reason why the drives won't mount. All three volumes might be damaged! Ubuntu won't mount damaged columes (volumes with inconsistencies). To fix that, go into windows and perform a disk check on all drives. For vfat volumes, you can stay in Linux and use the dosfsck tool. You might want to try this before all the rest!

---

### Post by cajunlibra on 2007-10-15
root@cajun:/home/cajun# sudo mount -a
[mntent]: warning: no final newline at the end of /etc/fstab
mount: special device /dev/sdb1 does not exist



sdb1 is my USB drive which is not connected nor has it been in a while.

I ran "Check Disk" on XP on the shared drive and it turned up no errors.

---

### Post by cajunlibra on 2007-10-15
root@cajun:/home/cajun# sudo vol_id /dev/sda1
ID_FS_USAGE=filesystem
ID_FS_TYPE=vfat
ID_FS_VERSION=FAT16
ID_FS_UUID=07D6-0316
ID_FS_UUID_ENC=07D6-0316
ID_FS_LABEL=DellUtility
ID_FS_LABEL_ENC=DellUtility
ID_FS_LABEL_SAFE=DellUtility
root@cajun:/home/cajun# sudo vol_id /dev/sda2
ID_FS_USAGE=filesystem
ID_FS_TYPE=ntfs
ID_FS_VERSION=3.1
ID_FS_UUID=CC58102058100C38
ID_FS_UUID_ENC=CC58102058100C38
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
root@cajun:/home/cajun# sudo vol_id /dev/sda3
ID_FS_USAGE=filesystem
ID_FS_TYPE=vfat
ID_FS_VERSION=FAT32
ID_FS_UUID=B833-06C0
ID_FS_UUID_ENC=B833-06C0
ID_FS_LABEL=SHARED
ID_FS_LABEL_ENC=SHARED
ID_FS_LABEL_SAFE=SHARED

---

### Post by vanadium on 2007-10-15
Your mount -a suggestst that it all is mounted without a problem. Your output of mount suggests nothing is mounted. What is the output when you mount manually?

sudo mount /dev/sda2

or

sudo mount /dev/sda2 /media/sda2

Try listing its contents

ls /media/sda2

Try unmounting it

sudo umount /media/sda2

---

### Post by cajunlibra on 2007-10-15
root@cajun:/home/cajun# sudo mount /dev/sda3 /home/cajun/shared
mount: /dev/sda3 already mounted or /home/cajun/shared busy
root@cajun:/home/cajun# sudo umount /home/cajun/shared
umount: /home/cajun/shared: not mounted
root@cajun:/home/cajun# sudo mount /dev/sda3 /home/cajun/shared
mount: /dev/sda3 already mounted or /home/cajun/shared busy
root@cajun:/home/cajun# sudo mount /dev/sda2 /media/sda2
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda2 ()
root@cajun:/home/cajun# ls /media/sda2
root@cajun:/home/cajun# sudo umount /media/sda2
umount: /media/sda2: not mounted
root@cajun:/home/cajun# sudo umount /dev/sda2
umount: /dev/sda2: not mounted
root@cajun:/home/cajun#


Any ideas how to move forward since manual mounting doesn't seem to work?

Thanks

---

### Post by vanadium on 2007-10-16
Better separate the problems: sda3 is a vfat volume and sda2 is an ntsf volume. Better debug one at the time. /dev/sda3 either is mounted or "busy" according to your output. Try mounting it manually in a freshly created directory, e.g.

sudo mkdir test
sudo mount /dev/sda3 test
ls test

If this works, then there must be a problem with your mount points being "busy", whatever that is. If you test and have error messages, time to google for these error messages to see what could be causing them.

---

### Post by cajunlibra on 2007-10-16
When using the kernel version 2.6.20-16 the drives mount perfectly fine. It's just when I boot up 2.6.22-14 that the drives aren't recognized.


root@cajun:/home/cajun# sudo mkdir sharedrive
root@cajun:/home/cajun# sudo mount /dev/sda3 /home/cajun/sharedrive
mount: /dev/sda3 already mounted or /home/cajun/sharedrive busy
root@cajun:/home/cajun# sudo umount /dev/sda3
umount: /dev/sda3: not mounted
root@cajun:/home/cajun# sudo mount /dev/sda3 /home/cajun/sharedrive
mount: /dev/sda3 already mounted or /home/cajun/sharedrive busy
root@cajun:/home/cajun#                  

I found the following in my /var/log/udev
UDEV  [1192578686.912596] add      /block/sda/sda3 (block)
UDEV_LOG=3
ACTION=add
DEVPATH=/block/sda/sda3
SUBSYSTEM=block
SEQNUM=1803
MINOR=3
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:1f.2/host0/target0:0:0/0:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
UDEVD_EVENT=1
DEVTYPE=partition
ID_VENDOR=ATA
ID_MODEL=FUJITSU_MHV2080A
ID_REVISION=0000
ID_SERIAL=1ATA_FUJITSU_MHV2080AH_NT24T632J9J0
ID_SERIAL_SHORT=ATA_FUJITSU_MHV2080AH_NT24T632J9J0
ID_TYPE=disk
ID_BUS=scsi
ID_ATA_COMPAT=FUJITSU_MHV2080AH_NT24T632J9J0
ID_PATH=pci-0000:00:1f.2-scsi-0:0:0:0
ID_FS_USAGE=filesystem
ID_FS_TYPE=vfat
ID_FS_VERSION=FAT32
ID_FS_UUID=B833-06C0
ID_FS_UUID_ENC=B833-06C0
ID_FS_LABEL=SHARED
ID_FS_LABEL_ENC=SHARED
ID_FS_LABEL_SAFE=SHARED
DEVNAME=/dev/sda3
DEVLINKS=/dev/disk/by-id/scsi-1ATA_FUJITSU_MHV2080AH_NT24T632J9J0-part3 /dev/disk/by-id/ata-FUJITSU_MHV2080AH_NT24T632J9J0-part3 /dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part3 /dev/disk/by-uuid/B833-06C0 /dev/disk/by-label/SHARED

---

### Post by vanadium on 2007-10-17
Then you found the cause of the issue. I am still running 2.6.20-16.

---

### Post by sirjimmus on 2007-10-20
I am having the same problem with Gutsy.  I could access my two NTFS drives (well one is a drive, one is split into NTFS and ext3 partition) easily through Places > Computer in Feisty but since upgrading it has not worked.

I have tried the instructions listed here and in another thread.

Output of fdisk -l
```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a555750

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         574     4610623+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *         575       30515   240501082+   7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14ce3228

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        3826       30508   214331166    7  HPFS/NTFS
/dev/sdb2               1        3662    29414983+  83  Linux
/dev/sdb3            3663        3825     1309297+  82  Linux swap / Solaris
/dev/sdb4           30509       30515       56227+   f  W95 Ext'd (LBA)
/dev/sdb5           30509       30515       56196    b  W95 FAT32

```

sda1 is the manufacturers recovery thing
sda2 is my windows partition
sdb1 is my other drive which has all my music etc on.

Following the instructions in this thread gets me:

```


sudo mount /dev/sda2 /media/sda2

Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /media/sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /media/sda2 ntfs-3g defaults,force 0 0



```

There are no external devices connected and I am at a bit of a loss.

---

