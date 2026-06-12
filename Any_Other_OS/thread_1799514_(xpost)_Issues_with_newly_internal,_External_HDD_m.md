---
title: "(xpost) Issues with newly internal, External HDD mounting"
date: 2011-07-07
forum: Any Other OS
---

### Post by anotheraddict on 2011-07-07
Hey guys, I'm getting the following error after trying to take my external Seagate Deskagent apart and installing it as a stand alone, internal drive.  

```
[INDENT]Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed
[/INDENT]
```

My mtab reads:
```
[INDENT]/dev/sdb1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/home/another/.Private /home/another ecryptfs ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=852fca49d18152ca,ecryptfs_fnek_sig=81a2c79e97d73c8a 0 0
gvfs-fuse-daemon /home/another/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=another 0 0
/dev/sdc1 /media/Games fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0[/INDENT]
```

And Fstab:
```
[INDENT]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=667fa044-0b40-4ac5-8062-4574fe905f09 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0[/INDENT]
```

Basically I had the HDD working as a emulated internal drive with windows 7, and before I made the decision to migrate to Ubuntu (actually Mint 11) I decided I would take that external and move it internally as I had no use for the portability.

Thanks for the taking the time to help, I'm at a loss without my data! (literally every bit of my entertainment :icon_frown:)

---

### Post by anotheraddict on 2011-07-07
any advice on where to even begin trying to fix this?  I'm currently at a loss

---

### Post by Perfect Storm on 2011-07-08
Moved to Other OS/Distro Talk.

---

### Post by DawieS on 2011-07-08
If you have solved the problem yourself, it would be better to mark the thread as solved, instead of inserting (FIXED) into the title of the first post. It still shows the original thread title in the main forum menu.

You can find it in "Thread Tools" on top.:wink:

---

### Post by anotheraddict on 2011-07-08
Well I somehow got it working for one night, through the use of Gparted, and the Disk Manager, but after restarting my pc, all of that was lost apparently.

<img src="http://i.imgur.com/feCr2.png" alt="" title="Hosted by imgur.com" />

This is what my disk manager looks like, any ideas anyone?  Its obviously getting mounted through the PATA controller, but there is no pata controller anymore, this is a SATA drive, hooked up through SATA like the rest of them.

---

### Post by anotheraddict on 2011-07-09
anything at all as to where I should look? tools to use?

---

### Post by DawieS on 2011-07-10
I cannot see what your Disk Manager looks like. All I see is "<img src="http://i.imgur.com/feCr2.png" alt="" title="Hosted by imgur.com" />", and I have checked that nothing is blocked on that page on my side.

Something wrong with the format?:wink:

---

### Post by Perfect Storm on 2011-07-10
> **DawieS said:**
> I cannot see what your Disk Manager looks like. All I see is "<img src="http://i.imgur.com/feCr2.png" alt="" title="Hosted by imgur.com" />", and I have checked that nothing is blocked on that page on my side.

Something wrong with the format?:wink:

The forum doesn't support <html> codes. Please use [BB Code]

---

### Post by mips on 2011-07-10
> **DawieS said:**
> I cannot see what your Disk Manager looks like. All I see is "<img src="http://i.imgur.com/feCr2.png" alt="" title="Hosted by imgur.com" />", and I have checked that nothing is blocked on that page on my side.

Something wrong with the format?:wink:

Just go to the URL,
[http://i.imgur.com/feCr2.png](http://i.imgur.com/feCr2.png)

I embedded the image here but took it out as it's to big. I cropped his image and also attached it below.

Post the output of *sudo fdisk -l* here.



.

---

### Post by anotheraddict on 2011-07-10
This is the fdisk output requested, don't understand how I corrected it for one night, but can't replicate the settings i had >.<

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe896429b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000db6d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29880   240005120   83  Linux
/dev/sdb2           29880       30402     4191233    5  Extended
/dev/sdb5           29880       30402     4191232   82  Linux swap / Solaris

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbeeeccea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30402   244196352    7  HPFS/NTFS

```

---

### Post by mips on 2011-07-10
Well something here does not add up.

The 1GB NTFS drive is seen as sda yet in your fstab you have:
```

/dev/sda1       /               ext4    errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
#UUID=667fa044-0b40-4ac5-8062-4574fe905f09 none        swap sw 0      

```

Which says your root & swap partitions reside on sda while mtab & fdisk say they are actually on sdb (which they are).

My suggestion would be to backup your /etc/fstab file and then rebuild it.

Maybe search here on how to rebuild the fstab file using UUIDs or look at this guide from 2009 [http://ubuntu-install.blogspot.com/2009/11/fstab-automatically-edited.html](http://ubuntu-install.blogspot.com/2009/11/fstab-automatically-edited.html)

---

### Post by anotheraddict on 2011-07-10
So awesome man, I was able to rewrite my fstab manually and that worked spot on!

I believe that there are still some issues to figure out though, such as my Disk Utility still seeing it as a PATA drive, under its own separate host Controller =(

I can live with that though, I'm just thrilled I can actually use my drive again.

Any advice as to where I would go to correct this incorrect PATA assignment?  other then that thank you so much guys

Should I change this to solved? or no since technically its still being incorrectly recognized?

---

