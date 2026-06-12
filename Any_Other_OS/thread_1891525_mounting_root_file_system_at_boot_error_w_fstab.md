---
title: "mounting root file system at boot: error w/ fstab"
date: 2011-12-05
forum: Any Other OS
---

### Post by Drone4four on 2011-12-05
I recently installed a Oneiric based Linux distro.  It booted fine until I changed my fstab.  I altered my fstab so I could access my ntfs and other Linux partitions.  Now when I boot in recovery mode, it hangs after 2 or 3 seconds with this message:

```

Begin: Running /scripts/init-premount &#8230; done
Begin:  Mounting root file system ...

```

And then it just hangs there forever until I press the reset button on my PC.  I figure that I am getting this error because I didn&#8217;t configure my fstab correctly.  Here is what my fstab looks like:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
/dev/sda7        /               reiserfs notail          0       1
# / was on UUID=ef73f69f-1518-4c85-967d-2ed64c157ef1 after installation
# swap was on /dev/sda6 during installation
UUID=7208caa3-3b2a-4134-a114-23cf92c1238d none            swap    sw              0       0
/dev/sda3        /home/winxp     ntfs-3g        defaults    0 0
/dev/sdb1        /home/ntfs2tb    ntfs-3g        defaults    0 0
/dev/sda2         /home/slack/    ext4        noatime     0 0
# deleted: /dev/sda5        /home/gentoo    ext3        noatime        0 0

```

Even if &#8216;/dev/sda7&#8217; is replaced with &#8216;UUID=ef73f69f-1518-4c85-967d-2ed64c157ef1&#8217;, I get the same error message on boot.  I foolishly didn't back up my fstab before changing it so I have nothing to revert back to.

I tried adding # to the beginning of all the lines in my fstab except the line for swap and for root.  My fstab therefore looks like this:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
#UUID=ef73f69f-1518-4c85-967d-2ed64c157ef1
/dev/sda7        /               reiserfs notail          0       1
# swap was on /dev/sda6 during installation
UUID=7208caa3-3b2a-4134-a114-23cf92c1238d none            swap    sw              0       0
# /dev/sda3        /home/winxp     ntfs-3g        defaults    0 0
# /dev/sdb1        /home/ntfs2tb    ntfs-3g        defaults    0 0
# /dev/sda2         /home/slack/    ext4        noatime     0 0
# deleted: /dev/sda5        /home/gentoo    ext3        noatime        0 0

```

With this fstab, it still chokes at boot at around the 3 second mark with the same error message.

Here is the output of parted -l and fdisk -l from my LiveDVD:

```
mint@mint ~ $ sudo parted -l
Model: ATA WDC WD3200AAKS-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  321MB   321MB   primary   ext2            boot
2      321MB   39.3GB  39.0GB  primary   ext4
3      39.3GB  78.3GB  39.0GB  primary   ntfs
4      78.3GB  320GB   242GB   extended
6      78.3GB  94.3GB  16.0GB  logical   linux-swap(v1)
7      94.3GB  218GB   124GB   logical   reiserfs
5      218GB   320GB   102GB   logical   ntfs


Model: ATA WDC WD20EARS-00J (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  2000GB  2000GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

mint@mint ~ $ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00087335

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      626534      313236   83  Linux
/dev/sda2          626535    76790699    38082082+  83  Linux
/dev/sda3        76790700   152954864    38082082+   7  HPFS/NTFS/exFAT
/dev/sda4       152954878   625135615   236090369    5  Extended
/dev/sda5       426477568   625135615    99329024    7  HPFS/NTFS/exFAT
/dev/sda6       152954880   184205311    15625216   82  Linux swap / Solaris
/dev/sda7       184207360   426477567   121135104   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000cc3

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001    7  HPFS/NTFS/exFAT
mint@mint ~ $

```

What am I doing wrong?

I tried posting in the Linux Mint forums, but no one has replied with a solution so I thought I would try on the Ubuntu forums.  I hope that's not a problem.

---

### Post by Drone4four on 2011-12-05
sudoman on FreeNode suggests that I change "1" to "0" under the "pass" column in the line for /dev/sda7 in my fstab. I'll try that now and report back to this thread after I reboot.

---

### Post by Drone4four on 2011-12-05
It didn't work.  Upon returning to my LiveCD environment, sudoman said:

> Drone4four: i take that back. it won't fix your problem. it just tells fsck the priority for checking the drive on boot up. as a matter of fact, 1 is a good value for that option on your / partition.

---

### Post by zeroti on 2011-12-05
> **Drone4four said:**
> sudoman on FreeNode suggests that I change "1" to "0" under the "pass" column in the line for /dev/sda7 in my fstab. I'll try that now and report back to this thread after I reboot.

I'm sudoman on freenode. Once i read about that option online, I told Drone4four that it won't do anything helpful here. And it's a good value since it tells fsck to check your drives every once in a while.

---

### Post by Perfect Storm on 2011-12-06
Moved to Other OS/Distro Talk.

---

### Post by lukeiamyourfather on 2011-12-06
Are you using reiserfs or resier4? Your current fstab is showing reiserfs (which refers to version 3).

---

### Post by Drone4four on 2011-12-06
> **lukeiamyourfather said:**
> Are you using reiserfs or resier4? Your current fstab is showing reiserfs (which refers to version 3).

I am using reiserfs not resier4, as the parted command and its output indicates in my initial post.

---

### Post by Drone4four on 2011-12-09
fdisk says that /dev/sda1 is set as the bootable partition.  So it would be reasonable to assume that it contains my ram image and kernel....but upon closer analysis -- with that drive mounted using my LiveCD -- the contents of /dev/sda1 mounted as /boot show that all the files are dated from early 2010, when I was playing around with Gentoo.  Check it:

```

mint@mint ~ $ sudo mount /dev/sda1 /boot
mint@mint ~ $ cd /boot/
mint@mint /boot $ ls
boot
grub
grub.bak
initramfs-genkernel-x86_64-2.6.30-gentoo-r4
kernel-genkernel-x86_64-2.6.30-gentoo-r4
lost+found
splash
System.map-genkernel-x86_64-2.6.30-gentoo-r4
mint@mint /boot $ cd grub
mint@mint /boot/grub $ ls
default           grub.conf.bak                  stage1
device.map        grub.conf.bakapril4-2010.conf  stage2
e2fs_stage1_5     iso9660_stage1_5               stage2_eltorito
fat_stage1_5      jfs_stage1_5                   ufs2_stage1_5
ffs_stage1_5      menu.lst                       vstafs_stage1_5
grub.conf         minix_stage1_5                 xfs_stage1_5
grub.conf~        reiserfs_stage1_5
grub.conf.backup  splash.xpm.gz
mint@mint /boot/grub $ ls -l
total 340
-rw-r--r-- 1 root root    197 2010-02-25 21:27 default
-rw-r--r-- 1 root root     30 2010-02-25 21:11 device.map
-rw-r--r-- 1 root root   8760 2010-02-25 21:27 e2fs_stage1_5
-rw-r--r-- 1 root root   7836 2010-02-25 21:27 fat_stage1_5
-rw-r--r-- 1 root root   7112 2010-02-25 21:27 ffs_stage1_5
-rw-r--r-- 1 root root    464 2010-03-09 01:20 grub.conf
-rw-r--r-- 1 root root    580 2010-03-09 01:20 grub.conf~
-rw-r--r-- 1 root root    527 2010-03-07 21:59 grub.conf.backup
-rw-r--r-- 1 root root    593 2010-03-08 02:14 grub.conf.bak
-rw-r--r-- 1 root root    464 2010-04-04 21:56 grub.conf.bakapril4-2010.conf
-rw-r--r-- 1 root root   7104 2010-02-25 21:27 iso9660_stage1_5
-rw-r--r-- 1 root root   8692 2010-02-25 21:27 jfs_stage1_5
lrwxrwxrwx 1 root root      9 2010-02-25 21:11 menu.lst -> grub.conf
-rw-r--r-- 1 root root   7328 2010-02-25 21:27 minix_stage1_5
-rw-r--r-- 1 root root   9732 2010-02-25 21:27 reiserfs_stage1_5
-rw-r--r-- 1 root root  33856 2010-02-25 21:10 splash.xpm.gz
-rw-r--r-- 1 root root    512 2010-02-25 21:27 stage1
-rw-r--r-- 1 root root 107892 2010-02-25 21:27 stage2
-rw-r--r-- 1 root root 107892 2010-02-25 21:10 stage2_eltorito
-rw-r--r-- 1 root root   7368 2010-02-25 21:27 ufs2_stage1_5
-rw-r--r-- 1 root root   6712 2010-02-25 21:27 vstafs_stage1_5
-rw-r--r-- 1 root root   9532 2010-02-25 21:27 xfs_stage1_5
mint@mint /boot/grub $ cd ..
mint@mint /boot $ ls -l
total 7776
lrwxrwxrwx 1 root root       1 2009-09-05 17:14 boot -> .
drwxr-xr-x 2 root root    1024 2010-04-04 21:56 grub
drwxr-xr-x 2 root root    1024 2010-02-25 21:05 grub.bak
-rw-r--r-- 1 root root 3491923 2010-03-08 02:01 initramfs-genkernel-x86_64-2.6.30-gentoo-r4
-rw-r--r-- 1 root root 2816128 2010-02-24 03:55 kernel-genkernel-x86_64-2.6.30-gentoo-r4
drwx------ 2 root root   12288 2009-09-05 16:36 lost+found
drwxr-xr-x 2 root root    1024 2010-03-07 21:59 splash
-rw-r--r-- 1 root root 1600763 2010-02-24 03:55 System.map-genkernel-x86_64-2.6.30-gentoo-r4
mint@mint /boot $

```

the contents of /boot in my lisa partition on /dev/sda7 looks like this:

```

mint@mint ~ $ cd /mnt/lisa/boot/
mint@mint /mnt/lisa/boot $ ls -l
total 21898
-rw-r--r-- 1 root root   730503 2011-10-07 20:02 abi-3.0.0-12-generic
-rw-r--r-- 1 root root   134754 2011-10-07 20:02 config-3.0.0-12-generic
drwxr-xr-x 3 root root     6288 2011-12-02 23:01 grub
-rw-r--r-- 1 root root 13804061 2011-12-03 01:31 initrd.img-3.0.0-12-generic
-rw-r--r-- 1 root root   176764 2011-05-02 23:07 memtest86+.bin
-rw-r--r-- 1 root root   178944 2011-05-02 23:07 memtest86+_multiboot.bin
-rw------- 1 root root  2694177 2011-10-07 20:02 System.map-3.0.0-12-generic
-rw------- 1 root root     1367 2011-10-07 20:08 vmcoreinfo-3.0.0-12-generic
-rw-r--r-- 1 root root  4658096 2011-11-24 19:13 vmlinuz-3.0.0-12-generic
mint@mint /mnt/lisa/boot $


```

Even with this in mind I decided to go ahead anyways, adding the following entry to my fstab:

```

/dev/sda1 /boot                   ext2    defaults        1 2

```

My new fstab therefore looked like this:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1 /boot                   ext2    defaults        1 2
# / was on /dev/sda7 during installation
UUID=1ad64730-ac97-42a3-8420-8e8707456937 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7208caa3-3b2a-4134-a114-23cf92c1238d none            swap    sw              0       0
/dev/sda3        /home/winxp     ntfs-3g        defaults    0 0
/dev/sdb1        /home/ntfs2tb    ntfs-3g        defaults    0 0
/dev/sda2         /home/slack/    ext4        noatime     0 0
# deleted: /dev/sda5        /home/gentoo    ext3        noatime        0 0

```

After rebooting my computer I discovered that, to no surprise, it didn’t help. D=

---

### Post by gordintoronto on 2011-12-10
> **Drone4four said:**
> I am using reiserfs...

Why? It's a dead end.

---

### Post by Drone4four on 2011-12-10
After bashing my head against the wall for several days and after troubleshooting on 3 different forums and in ##linux on FreeNode, the only solution was to reinstall Lisa.  Ugh. 

gordintoronto: I decided to go with ReiserFS because I had a falling out with ext4 that I document in [this thread]("http://forums.linuxmint.com/viewtopic.php?f=46&t=86709").  

The experts in ##Linux hypothesized that my problem could have been ReiserFS related, so I went with ext4 upon reinstall.  No problems so far.

---

