---
title: "Need automount help."
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-12-08
The first time I installed Ubuntu 6.06 my 3 Windows NTFS partitions got automounted.  Then I had to re-install Windows several times followed by an filesystem changeover to FAT32.  
After these things my Windows partitions didn't get automounted, yet they are still the same size and in the exact same positions.  It's just the NFTS to FAT32 factor that has changed.

How should I use fstab to correct the altered filesystems?
HELP!

---

### Post by SyvanX on 2006-12-08
What does your fstab file currently look like?

Post the outputs of these two commands

```
cat /etc/fstab
sudo fdisk -l
```

I'm guessing you just need to change the filesystem type in fstab from ntfs to vfat or auto

---

### Post by jingo811 on 2006-12-09
1 character. :rolleyes: 
> mike@sanka:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hdb1       /media/**hdb1**     **vfat **   defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
mike@sanka:~$My hdb1 was originally a NTFS but I changed it to vfat in nano but nothing much happened.  By following psychocats tutorial partially I'm guessing my numbers should also be altered?

> mike@sanka:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1278    10265503+   c  W95 FAT32 (LBA)
/dev/hda2            1279        3831    20506972+   c  W95 FAT32 (LBA)
/dev/hda3            3832        4998     9373927+  83  Linux

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/**hdb1**               1         131     1052226    b  W95 FAT32
/dev/hdb2             132         261     1044225   82  Linux swap / Solaris
/dev/hdb3             262        4998    38049952+  83  Linux
mike@sanka:~$


---

### Post by taurus on 2006-12-09
I don't understand what you mean when you say you change /dev/hdb1 from ntfs to fat32 using nano!!!  Nano is just a basic text editor in Linux so it can't change filesystem from one type to another...  What if you have this line for /dev/hdb1 in your /etc/fstab instead?

```

/dev/hdb1  /media/hdb1  vfat  nls=utf8,umask=000   0   0

```

p.s.  Both of your /dev/hda1 & /dev/hda2 are fat32 so I don't know why you mount them as ntfs!

---

### Post by SyvanX on 2006-12-09
It looks like he had reinstalled his ntfs windows install with a fat32 windows install after installing Ubuntu.  So his fstab was still referencing his /dev/hda partitions as ntfs.

in your /etc/fstab file, change ntfs to vfat for /dev/hda1, /dev/hda2 and /dev/hdb1 using taurus's line.

[QUOTE=taurus]```
/dev/hdb1 /media/hdb1 vfat defaults,nls=utf8,umask=000 0 0
```[/QUOTE]

Then, to test, just run

```
sudo mount /media/hda1
```

---

### Post by jingo811 on 2006-12-11
> mike@sanka:/etc$ sudo nano /etc/fstab
Password:
mike@sanka:/etc$ sudo mount /media/hdb1
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mike@sanka:/etc$
I only tested my hdb1 partition so far for fear of doing something really destructuve.  But it seems things didn't go so well from above Error message.
What the next step?
I also took out a snippet by doing the dmesg command that might help find the problem
> [17183574.416000] FAT: Unrecognized mount option "nls=utf8" or missing value


> 
mike@sanka:/etc$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hdb1       /media/hdb1     vfat    defaults,nls=utf8,umask=000 0 0
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
mike@sanka:/etc$


---

### Post by jingo811 on 2006-12-11
Bumparama!
bump2

---

### Post by jingo811 on 2006-12-17
bump 2.

---

### Post by chettyk on 2006-12-17
> **jingo811 said:**
> bump 2.

Try to mount the windows partitions from the terminal window (Applications > Accessories > Terminal). 

I'd also suggest that you create a new directory under /media. Then you can use this new directory as the mount point to experiment with mounting various partitions. To create a new directory under /media, say calling it 'windows':
```
sudo mkdir /media/windows
```

Then try a simple mount command from the terminal. If you want to mount /dev/hdb1:
```
sudo mount /dev/hdb1 /media/windows
```

Do you still get an error?

---

### Post by jingo811 on 2006-12-17
Well I could always access the partitions manually but I want them to load automatically and show on my Desktop like before when I installed Ubuntu after Windows.  Before I changed the filesystem from NTFS to FAT32 and re-installed Windows after my Ubuntu.

---

### Post by chettyk on 2006-12-17
> **jingo811 said:**
> Well I could always access the partitions manually but I want them to load automatically and show on my Desktop like before when I installed Ubuntu after Windows.  Before I changed the filesystem from NTFS to FAT32 and re-installed Windows after my Ubuntu.

According to your fdisk -l output, there are there are three partitions that appear as FAT32. But in your fstab only one drive -- /dev/hdb1 -- has been changed to vfat. It could therefore be the other two partitions that are the problem.

If you can mount all the three partitions manually, then change the fstab entires for /dev/hda1 and /dev/hda2 as well. 

If you are worried about mucking up your fstab file, make a backup copy of it before modifying it. (That is a precaution I routinely take before changing any configuration file.)

After you have saved the modified fstab file, do:
```
df -h
```

That will show you which partitions are currently mounted. If any of the vfat partitions are mounted, umount them. Then try:
```
sudo fdisk -a
```

---

### Post by jingo811 on 2006-12-17
> mike@sanka:~$ [B]clear
[/B]
mike@sanka:~$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     vfat    defaults,nls=utf8,umask=000 0 0
/dev/hda2       /media/hda2     vfat    defaults,nls=utf8,umask=000 0 0
/dev/hdb1       /media/hdb1     vfat    defaults,nls=utf8,umask=000 0 0
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
mike@sanka:~$ [B]sudo fdisk -l
[/B]
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1278    10265503+   c  W95 FAT32 (LBA)
/dev/hda2            1279        3831    20506972+   c  W95 FAT32 (LBA)
/dev/hda3            3832        4998     9373927+  83  Linux

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         131     1052226    b  W95 FAT32
/dev/hdb2             132         261     1044225   82  Linux swap / Solaris
/dev/hdb3             262        4998    38049952+  83  Linux
mike@sanka:~$ **sudo mount /media/hda1**
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mike@sanka:~$ **df -h**
Filesystem            Size Used Avail Use% Mounted on
/dev/hda3             8.8G  2.8G  5.7G  33% /
varrun                506M   80K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  140K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-27-386/volatile
/dev/hdb3              36G  8.3G   26G  25% /home
/dev/hdc              678M  678M     0 100% /media/cdrom0
mike@sanka:~$ **sudo fdisk -a**
fdisk: invalid option -- a

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
mike@sanka:~$

The plot thickens and I'm nowhere close to the answer :-k  Do I need to do a super secret reboot routine of some sort to make it work perhaps?

---

### Post by chettyk on 2006-12-17
> **jingo811 said:**
> The plot thickens and I'm nowhere close to the answer :-k  Do I need to do a super secret reboot routine of some sort to make it work perhaps?

You probably don't need a "super secret reboot routine", but you'll need patience to find out what the problem is and to fix it.

Backup your fstab file and make the following changes to the lines dealing with the FAT32 partitions:
```
# /dev/hda1 /media/hda1 vfat defaults,nls=utf8,umask=000 0 0
# /dev/hda2 /media/hda2 vfat defaults,nls=utf8,umask=000 0 0
/dev/hdb1 /media/hdb1 vfat defaults 0 0

```

I have put hash-marks at the beginning of the fstab lines dealing with hda1 and hda2. As a result, those lines will appear to be merely comments and those partitions will not be mounted. That way, any errors during the mounting of FAT32 partitions will be because of hdb1 alone.

As for the line dealing with hdb1, I found that the original line in the fstab for my laptop that I dual-boot with XP goes:
/dev/hda1       /media/windows  ntfs    defaults                0       0
When I use that line, my NTFS partition gets automounted when Linux boots. 

After you finished making and saving the changes to fstab, do 
```
sudo mount -a
```

At this point, you are only checking if the the hdb1 partition auto-mounts correctly. You may not be able to write to that partition as an ordinary user. But that can be changed once you know that auto-mounting works.

---

### Post by jingo811 on 2006-12-18
It worked tnx chettyk.

---

### Post by chettyk on 2006-12-18
> **jingo811 said:**
> It worked tnx chettyk.

Great. I have been wondering why the previous fstab lines didn't work. If you remember, they were:
```
/dev/hda1 /media/hda1 vfat defaults,nls=utf8,umask=000 0 0
/dev/hda2 /media/hda2 vfat defaults,nls=utf8,umask=000 0 0
/dev/hdb1 /media/hdb1 vfat defaults,nls=utf8,umask=000 0 0
```

[URL="http://wiki.ubuntu.com"]
[COLOR="Red"]_Ubuntu Wiki_[/COLOR][/URL] -- which is a great resource -- has an entry for [[COLOR="Red"]_automatically mounting windows partitions_[/COLOR]]("https://help.ubuntu.com/community/AutomaticallyMountPartitions"). According to that page, the option 'nls=utf8' is for the NTFS partitions used by Windows XP, not for vfat partitions.

A page in the website [Debian Admin]("http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html") , which I found through Google, indicates that the following entry should auto-mount the vfat partitions and allow users read-write access to the partition:
```
/dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000 0 0
/dev/hda2 /media/hda2 vfat iocharset=utf8,umask=000 0 0
/dev/hdb1 /media/hdb1 vfat iocharset=utf8,umask=000 0 0
```

So if read-write access is not possible with your existing fstab, you could back it up and try modifying it as above.

---

