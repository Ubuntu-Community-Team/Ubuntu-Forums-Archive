---
title: "Change permissions of Windows partitions"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by sahilsapre on 2007-08-09
I'm completely new to linux and unsure of which category this post should fall in, but here goes..
I mounted my windows drives (C drive and D drive) which are /dev/sda1 and /dev/sda5 into /media/win and /media/wind. When I try to access these folders through the GUI file explorer, it says I don't have permissions to access them since I'm not logged in as root. How do I change them?

---

### Post by p_quarles on 2007-08-09
I'm assuming you're using a Windows version later than 2K. If I'm correct, then you have an NTFS filesystem, and need to install the software that allows you full access to those partitions:
```
sudo apt-get install ntfs-3g
```
Once that's done, go to Applications >> System Tools >> NTFS configuration. From there, you'll be able to configure your Windows drives for full read/write permissions.

---

### Post by vexorian on 2007-08-09
I reccomend you though that you only keep the read permission and only enable (manually) the write permission when you need it.

The reason is that if windows crashed or required a reboot, you would have some  issues when ubuntu will try to mount the partitions next time, and viceversa. So if you don't want to deal with annoyances it is better to enable and disable write when necessary...

---

### Post by sahilsapre on 2007-08-10
ok..but HOW do i change the permissions whenever necessary?? That's the part I don't get! And thanks for the software, I'll check it out...

---

### Post by Hopeless on 2007-08-10
Hi,

sudo chown -R USERNAME:USERNAME /media/mynewdrive

---

### Post by Pas_sa on 2007-08-10
I managed to fix my booting problem and am back in Ubuntu - but now I can't write to my Windows partitions, only one of them lets me write to it. It has something to do with my order of partitions.. so my question really is:

How can I sort of.. refresh.. the ntfs-3g drivers so I get write support to NTFS back?

Thanks.. I have tried reopening it and enabling/disabling BTW.

---

### Post by Ek0nomik on 2007-08-10
You will want to make sure you shut down Windows nicely, which I am assuming you did, but just incase.  :)

Can you post your output of these commands as well:

```
sudo fdisk -l
sudo mount
cat /etc/fstab
```

A lot of people on this forum have experience with NTFS-3G, so hang tight.  :)

---

### Post by vexorian on 2007-08-10
> **sahilsapre said:**
> ok..but HOW do i change the permissions whenever necessary?? That's the part I don't get! And thanks for the software, I'll check it out...
After installing ntfs-3g you can go to applications\system tools\NTFS config tool and that will do everything for you, then you will have that place with a checkbox to enable write support.

---

### Post by bodhi.zazen on 2007-08-10
Threads merged. Same question, same answer :


> **Hopeless said:**
> Hi,

sudo chown -R USERNAME:USERNAME /media/mynewdrive

That does not work with FAT/NTFS partitions.

You need to set ownership and permissions at the time of mounting or with ntfs-config

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by Pas_sa on 2007-08-10
No, you shouldn't have merged the threads, the problem is *different*.

I had NTFS-3G working BEFORE. I formatted Windows. The partition numbers are slightly different. I need to restore write support.** It worked before**.

---

### Post by bodhi.zazen on 2007-08-10
> **Pas_sa said:**
> No, you shouldn't have merged the threads, the problem is *different*.

I had NTFS-3G working BEFORE. I formatted Windows. The partition numbers are slightly different. I need to restore write support.** It worked before**.

I am sorry you feel that way, but I only know of one way to set permissions and I do not know how "formatting windows" would change that so I merged your thread to save myself from typing the same answer to your question in two seemingly similar threads.

what did you do exactly ? what does "formatted windows" mean ? you made a new partition ? you installed windows ?

what does "The partition numbers are slightly different" mean ? you might need to update your fstab.

can you post the output of :

sudo fstab -l 

and the contents of /etc/fstab?

---

### Post by Pas_sa on 2007-08-10
sudo: fstab: command not found

and there is nothing in etc/fstab


Sorry for losing it there, just very frustrated at my PC atm. I upgraded the CPU and mobo, and upon rebooting of course I had to format Windows. Windows setup got into a furore about my partition numbering and I had to do a full backup of my other partitions so I could setup a 60GB partition to be used for Windows but still get it to use the letter C for that partition.

The numbering of partitions changed in the process. They are in different positions on the HDD as they were recreated. They also have different numbers (ie Ubuntu used to detect my system partition as sda5).

What I need is a way to remove all these old mounts that no longer work, then mount all my new 500GB drive partitions, then enable NTFS-3G, which is installed but does not work now for some reason.

Thanks.

---

### Post by bodhi.zazen on 2007-08-10
doh #-o

I was typing tooooo fast

sorry 'bout that

the command should be :

```
sudo fsdisk -l
```

^^ That is a smalll "L" and not a 1 

and to see the contents of fstab :

```
cat /etc/fstab
```

we forgot the leading / in /etc/fstab

:lolflag:

No need to apologize, we are here to help and understand frustration. I was just trying to explain my thoughts in merging your thread is all.

---

### Post by Pas_sa on 2007-08-10
sudo: fsdisk: command not found

and

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=f22052dc-0ba6-4478-98ac-08b0305b6179 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=10EE7C53EE7C3358 /media/sda2 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sda3 :
UUID=6AD0BDE7D0BDBA21 /media/sda3 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=CC44983144981FEE /media/sda5 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sdb2 :
UUID=c7eb87ad-296f-422d-9838-7b160afbb0a9 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda5 /media/System ntfs-3g defaults,locale=en_AU.UTF-8 0 0
/dev/sda2 /media/Games ntfs-3g defaults,locale=en_AU.UTF-8 0 0

```

---

### Post by Pas_sa on 2007-08-11
Super duper bump..

---

### Post by bodhi.zazen on 2007-08-11
LOL

```
sudo fdisk -l
```

BUT you can skip to editing fstab :

In a terminal type :

```
gksu gedit /etc/fstab
```

Make these changes :

> # /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=f22052dc-0ba6-4478-98ac-08b0305b6179 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
**/dev/sda2** /media/sda2 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sda3 :
UUID=6AD0BDE7D0BDBA21 /media/sda3 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
**/dev/sda5** /media/sda5 ntfs-3g defaults,locale=en_AU.UTF-8 0 1
# Entry for /dev/sdb2 :
UUID=c7eb87ad-296f-422d-9838-7b160afbb0a9 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda5 /media/System ntfs-3g defaults,locale=en_AU.UTF-8 0 0
/dev/sda2 /media/Games ntfs-3g defaults,locale=en_AU.UTF-8 0 0

Save and exit fstab

Then re-mount :

```
sudo mount -a
```

Now, you may have changed the partition numbers, if so, you will need to adust (see the output of sudo fdisk -l)

If you want to mount via UUID, list your devices with : ```
sudo blkid
``` and replace /dev/sdxy (in /etc/fstab) with UUID=xxx.yyy.zzz

---

### Post by bwtranch on 2007-08-11
Re: #6 please dont use caps, that will screw up new users for sure.

---

### Post by Pas_sa on 2007-08-11
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        7649    61432560    f  W95 Ext'd (LBA)
/dev/sda2   *        7650       35248   221688967+   7  HPFS/NTFS
/dev/sda3           35249       60801   205254472+   7  HPFS/NTFS
/dev/sda5               2        7649    61432528+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14344   115218148+  83  Linux
/dev/sdb2           14345       14593     2000092+  82  Linux swap / Solaris
andrew@andrewdesktop:~$ 


```

In response to your post.. I kind of get what you're saying for me to do.. but now I've also realised I have duplicate mounts everywhere..

After making the changes you said, the mounts still don't have NTFS write support, but seem to link up correctly (however I still have the games/system duplicates, even after deleting them from fstab..

---

