---
title: "Permissions going haywire - FAT32 Ext. Drive"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-07-29
I've got a 250GB USB Drive which was formatted to FAT32 on a windows machine. I mounted this through fstab and it worked fine for transferring data to my macs and pcs.

One day - it just appeared as PB_SAFE on my desktop and macs/pcs will no longer read it. My main problem at the moment however is that when I turn it on I have full read/write access. but within a few minutes the file permissions somehow change and suddenly I won't have access to delete files from a certain folder. and within 5 minutes the entire drive is read-only.


I haven't got a clue whats going on - help

:confused::confused:

Cheers,

---

### Post by aysiu on 2007-07-29
No clue what's going on.

I don't even know if it *can* be solved, but if there's even the possibility of solving it, we'll need more information.

Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
sudo fdisk -l
df -h
cat /etc/fstab
``` Then copy and paste the output back here.

---

### Post by auraithx on 2007-07-29
```
glasgowm@glasgowm-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3249    26097561   83  Linux
/dev/sda2   *        3250        4789    12370050   83  Linux
/dev/sda3            4790        4863      594405    5  Extended
/dev/sda5            4790        4863      594373+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9726    78124063+  83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    c  W95 FAT32 (LBA)
glasgowm@glasgowm-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              12G  6.4G  4.7G  58% /
varrun                252M  112K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M  120K  252M   1% /proc/bus/usb
udev                  252M  120K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1              74G   36G   35G  51% /media/hd2
/dev/sda1              25G   14G  9.9G  59% /media/disk
/dev/sdc1             233G  146G   88G  63% /media/external1
glasgowm@glasgowm-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=48a5c72f-651c-46ff-9878-55bbafa88a24 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=99f16eda-b35b-48fe-9f76-38fbd77958f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sdc1       /media/external1 vfat user,umask=0000
/dev/sdb1       /media/hd2     ext3 user,defaults        0       2

```
I've found a way to replicate the drive locking. It'll all work fine until I turn on hidden folders and try to delete .Trash-glasgowm. I'll get a "cannot delete x file as it is a read only file" then when I click any other folder after that the little locked sign appears at the top-right of the folder and the entire drive will be that way.

It won't let me delete the folder from root either.

---

### Post by aysiu on 2007-07-29
Well, it looks good for the most part. I haven't seen this problem recently, but about a year or so ago, there were still some weird problems with FAT32 if it was mounted within the /media directory. Can you try mounting it outside of that directory and also adding in the iocharset parameter on the /etc/fstab file?

**Step 1**
Back up your /etc/fstab file ```
sudo cp /etc/fstab /etc/fstab.backup
```

**Step 2**
Unmount the drive ```
sudo umount /media/external1
```

**Step 3**
Create a new mount point ```
sudo mkdir /external1
```

**Step 4**
Modify the /etc/fstab file ```
sudo nano /etc/fstab
``` Replace this line ```
/dev/sdc1       /media/external1 vfat user,umask=0000
``` with this line ```
/dev/sdc1       /external1 vfat iocharset=utf8,umask=000
``` Save (Control-X, Y, Enter)

**Step 5**
Remount ```
sudo mount -a
```

**Step 6**
Check it out. Go to the /external1 directory

Alternatively, if it really is an external drive (as the mount point name seems to indicate), delete that ```
/dev/sdc1       /media/external1 vfat user,umask=0000
``` line from the /etc/fstab altogether and let it just mount automatically the way any hotplugged device would.

---

### Post by auraithx on 2007-07-29
Removing it from the fstab all together seemed to fix it. - It's now mounting, but all the files are still read only :/

---

### Post by aysiu on 2007-07-29
That's weird, but it does seem to go along with the problem you had in the first place. *sudo fdisk -l* seems to indicate that /dev/sdc1 is FAT32, but when you mount it, it appears not to be. Can you post the output of that command? ```
dmesg | tail
```

---

### Post by auraithx on 2007-07-29
glasgowm@glasgowm-desktop:~$ dmesg | tail
[283179.805634] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[283179.806739] sdc: Write Protect is off
[283179.806747] sdc: Mode Sense: 27 00 00 00
[283179.806750] sdc: assuming drive cache: write through
[283179.806756]  sdc: sdc1
[283179.833451] sd 46:0:0:0: Attached scsi disk sdc
[283179.833521] sd 46:0:0:0: Attached scsi generic sg4 type 0
[283296.311770] FAT: Filesystem panic (dev sdc1)
[283296.311779]     fat_get_cluster: invalid cluster chain (i_pos 0)
[283296.311784]     File system has been set read-only

---

### Post by aysiu on 2007-07-29
This is a bit out of my league, but a Google search on part of the output turned up [this page](https://answers.launchpad.net/ubuntu/+question/3620), which may help you.

---

### Post by auraithx on 2007-07-29
Looks like it's Azureus' fault.

If I were to format my drive - what is the best format that is recognizable by all OS' (xp/macos/linux)

cheers

---

