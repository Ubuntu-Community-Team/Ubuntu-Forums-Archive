---
title: "Mounting issues. Arg!"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by erfunath on 2007-06-09
Alright, I've looked through everything I can find on these forums and other linux documentation about mounting drives, but I still can't seem to get mine to mount after trying.

I have an 80gb internal that's partitioned with 6gb ext3 for Ubuntu, 50-some-odd gigs for Windows XP, 6gb ntfs for documents so I can share them between the Ubuntu and Windows XP operating systems, and of course a 256mb swap partition.

I'm trying to mount that 6gb ntfs drive in Ubuntu, and I got it to automount to begin with. I renamed it Documents, and it showed up on the desktop and in /media/Documents. Then I found out it was read-only. After several hours of messing with fstab (which I backed up), I still can't get it to mount as read-write. Then I right-clicked and got into the drive options and added (under the Volume tab) "rw" to the mount options. Of course, now it won't mount at all, telling me that I have an invalid mount option selected. I can't figure out how to edit those mount options again, and I'm completely stumped, as you can imagine. I am, yes, one of those linux noobs that got himself into this a little too fast.

Anyway, here's fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=bcd7cb44-17be-4c90-adce-5399dea21a36 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=88715d1e-b179-4948-94fc-ed3ffa6fb571 /media/hda2     ntfs    defaults,rw        0       0
# /dev/hda3
UUID=C47CF79E7CF78A06 /media/hda3     ntfs    defaults,rw        0       0
# /dev/hda4
UUID=613f2cd9-4a59-4e9a-af24-352caf67f70d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I changed the ext3 on hda2 to ntfs, which is reflected above. That didn't make a difference at all. I changed the errors=ro to rw, and that didn't help. The sixth parameter (now a 0) was a 1, so I changed that too. No effect on the drive. At one point, I tried changing /media/hda2 to /media/Documents, and that had no effect either, so I just put it back.

Help, please!

---

### Post by taurus on 2007-06-09
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by erfunath on 2007-06-09
Thanks for responding so quick!

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         698     5606653+  83  Linux
/dev/hda2             731        1459     5855692+   7  HPFS/NTFS
/dev/hda3   *        1460        9728    66420742+   7  HPFS/NTFS
/dev/hda4             699         730      257040   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 60.0 GB, 60040544256 bytes
240 heads, 63 sectors/track, 7755 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7755    58627768+   7  HPFS/NTFS

```

---

### Post by Bachstelze on 2007-06-09
No need to be an expert to notice the UUID you entered doesn't seem good, it doesn't look like the others *at all* !

To see the correct UUID for your partition :

```
blkid
```

Alternatively, the old /dev/* notation still works.

---

### Post by erfunath on 2007-06-09
I didn't enter those, that's the way they were when I found them. What am I to do with this info?

```
/dev/hda1: LABEL="Ubuntu" UUID="bcd7cb44-17be-4c90-adce-5399dea21a36" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda2: TYPE="ntfs"
/dev/hda3: TYPE="ntfs"
/dev/hda4: TYPE="swap" UUID="613f2cd9-4a59-4e9a-af24-352caf67f70d"
/dev/sda1: TYPE="ntfs"

```

---

### Post by Bohlio on 2007-06-09
install ntfs-3g, then mount your partition by typing 
```
sudo mount -t ntfs-3g /dev/xxx /media/yyy
```
and then adding 
```
/dev/xxx /media/yyy ntfs-3g defaults 0 0
```
to your fstab. delete the existing line that you have for that partition, and change xxx to whatevery your device is, and change yyy to wherever you want it mounted in media.

---

### Post by Bachstelze on 2007-06-09
> **erfunath said:**
> I didn't enter those, that's the way they were when I found them. What am I to do with this info?

```
/dev/hda1: LABEL="Ubuntu" UUID="bcd7cb44-17be-4c90-adce-5399dea21a36" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda2: TYPE="ntfs"
/dev/hda3: TYPE="ntfs"
/dev/hda4: TYPE="swap" UUID="613f2cd9-4a59-4e9a-af24-352caf67f70d"
/dev/sda1: TYPE="ntfs"

```

Seems your NTFS doesn't have an UUID, just go back to the old /dev/* notation.

---

### Post by erfunath on 2007-06-09
I presume this is what you meant. Now it says I'm not priviledged to mount it.

Here's the new fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1 /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2 /media/hda2     ext3    defaults        0       0
/dev/hda3 /media/hda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by Bachstelze on 2007-06-09
You needed to go back to /dev/* only for your NTFS partition but it doesn't really matter.  Now, read on for info about how to properly mount it :)

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Bohlio on 2007-06-09
add "ntfs-3g" like i have in my example. Are we talking about hda2 or hda3?
and did you change hda2 from NTFS to ext3? cause thats what it looks like, unless im confused.

---

### Post by erfunath on 2007-06-09
We're talking about hda2. I have had ntfs file systems loaded on here before and been able to read, but never write.

I think I fixed the priviledge issue by using sudo. Then it said it couldn't find an ext3 filesystem, so I changed the fstab to reflect that there's ntfs on it. Then it mounted to /media/Documents, but it said I didn't have permissions to read that directory, so I tried sudo chmod a+rwx on it, but it said read-only file system. So I tried changing the mount parameters to include rw. Here's the fstab now.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1 /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2 /media/Documents     ntfs    defaults,rw        0       0
/dev/hda3 /media/hda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

edit: That ext3 was an error, I put it back to ntfs. The /media/Documents shows up, but there's nothing in it an chmod doesn't have any effect.

---

### Post by Bachstelze on 2007-06-09
Read the link I posted in my last message, it has everything you need.

---

### Post by taurus on 2007-06-09
If you want to write to ntfs filesystem, you need to install and use ntfs-3g instead of ntfs.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Bohlio on 2007-06-09
You need to install NTFS-3G, then manually mount your partition by typing ```
sudo mount -t ntfs-3g dev/hda2 /media/Documnets
``` Then I think you need your fstab to look like this 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1 /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2 /media/Documents     ntfs-3g    defaults        0       0
/dev/hda3 /media/hda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
 Notice the "ntfs-3g" in the fstab that is necessary to get it to mount automatically.

Edit: and is that cdrom entry in there causing you to have a "ghost" cd drive under Places>Computer while running kernel 16? If so, deleting that line will fix it.

---

### Post by erfunath on 2007-06-09
I'm using Feisty Fawn, so the ntfs-3g is already installed in the universe repository (whatever that is) according to that link. Now (when I put ntfs-3g in instead of ntfs):

```
nathan@Alexander:~$ sudo mount /dev/hda2
mount: unknown filesystem type 'ntfs-3g
```

---

### Post by Bohlio on 2007-06-09
```
sudo apt-get install ntfs-3g
```
The repository is in the universe so you dont have to add one, But you still need to install it. :-)

---

### Post by taurus on 2007-06-09
It is available from the universe repos but you need to install it first before you can use it.

```
sudo aptitude update
sudo aptitude install ntfs-3g ntfs-config
```

---

### Post by drowner on 2007-06-09
> **erfunath said:**
> I'm using Feisty Fawn, so the ntfs-3g is already installed in the universe repository (whatever that is) according to that link. Now (when I put ntfs-3g in instead of ntfs):

```
nathan@Alexander:~$ sudo mount /dev/hda2
mount: unknown filesystem type 'ntfs-3g
```

You need to READ it properly.

And don't skip down.

The reopsitory is an online place where you can download programs for installation. They are not installed by default.

What that site says is that NTFS-3g is available for download and installation by default in Feisty, that is, you dont need to modify the repositories.

So, go back, follow the steps, install it, and try again.

---

### Post by Bohlio on 2007-06-09
on a small side note, is there a difference between "apt-get" and "aptitude"?

---

### Post by erfunath on 2007-06-09
Okay, now I have the ability to read the drive after going through ntfs-config. Here's the fstab:
```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda2 /media/Documents ntfs umask=222,utf8 0 0
/dev/hda3 /media/hda3 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/hda4 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
```

It says I can't write to it because I don't have the right permissions. How do I go about making myself able to write to it now?

Sorry about all this, I'm sure this is frustrating for you guys, but thanks for the help!

---

### Post by Bohlio on 2007-06-09
On your hda2 line, Change ntfs to ntfs-3g.

And dont worry, It was a little confusing for me too when i set my ntfs partition up :-)

---

### Post by drowner on 2007-06-09
If you have installed ntfs-3g and nftfs config, you need to go back and edit your fstab properly.

it needs to say 'ntfs-3g', remember?

---

### Post by erfunath on 2007-06-09
Alright, I finally got it. This is what the fstab looks like, should another noob run around here like me and not find anything.

```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda2 /media/Documents ntfs-3g rw 0 0
/dev/hda3 /media/hda3 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/hda4 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

```

Thanks a ton, guys! :)

---

### Post by Bohlio on 2007-06-09
there ya go! :-) After a while you get used to these kinda things. All you gotta remember is that whenever you get directions, either from a person or from a how-to, you follow them exactly otherwise the smallest little thing can set you off :-) Glad to hear you got it working!

---

### Post by erfunath on 2007-06-09
Yeah, my problem is that I read to fast. Sorry 'bout that!

---

### Post by johntkucz on 2007-06-21
your thread seemed to have very similar problems as I was having, but I don't get the boot disk after blkid; here's the code:

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9376    75312688+  83  Linux
/dev/hda2            9377        9729     2835472+   5  Extended
/dev/hda5            9377        9729     2835441   82  Linux swap / Solaris

Disk /dev/sda: 1021 MB, 1021312512 bytes
129 heads, 16 sectors/track, 966 cylinders
Units = cylinders of 2064 * 512 = 1056768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         967      997367+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(972, 128, 16) logical=(966, 57, 15)

Disk /dev/sdc: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7872     2015216    e  W95 FAT16 (LBA)

Disk /dev/sdd: 517 MB, 517341184 bytes
218 heads, 45 sectors/track, 103 cylinders
Units = cylinders of 9810 * 512 = 5022720 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         103      505192+   b  W95 FAT32

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001    c  W95 FAT32 (LBA)

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:/boot$ blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="TravelDrive" UUID="392C-62FA" TYPE="vfat" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="TRAVEL2GB" UUID="D4BB-92EF" TYPE="vfat" 
/dev/sdd1: LABEL="JTK_IPOD" UUID="0000-0000" TYPE="vfat" 
/dev/sdf1: LABEL="My Book" UUID="92A8-ABE1" TYPE="vfat" 
ubuntu@ubuntu:/boot$ 


Please help! I need to get files off of dev/hda1
from 
/dev/hda1   *           1        9376    75312688+  83  Linux
/dev/hda2            9377        9729     2835472+   5  Extended
/dev/hda5 

How can I do that?

---

