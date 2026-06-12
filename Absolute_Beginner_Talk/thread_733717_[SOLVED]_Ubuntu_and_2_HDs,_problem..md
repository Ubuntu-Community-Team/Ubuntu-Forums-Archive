---
title: "[SOLVED] Ubuntu and 2 HDs, problem."
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Nerdriot on 2008-03-24
Hello,

Ok, so I have 2 HDs, and one has Windows XP (soon to be removed), and Ubuntu 7.10 on it, and the other has extra stuff.

The problem is, when I boot up in Ubuntu, I can view the "extras" HD, but I can't view the stuff on the Windows XP partition, on the same HD as Ubuntu.

Anyone know why that may be? I had Ubuntu and Winxp set up on one HD on another computer, and was able to view all the files on the Windows partition, but it's not working on this computer... :(

EDIT: Here's the output for "mount". I noticed an error in ext3...

```
ben@ubuntubox:/media/sdb1$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sdb2 on /media/sdb2 type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

```

---

### Post by kpkeerthi on 2008-03-24
Post the output of
```
sudo fdisk -l
```
and
```
cat /etc/fstab
```

---

### Post by keratos on 2008-03-24
your system is setup only that the root user 1000 or anyone in group 46 can use the device, but not specifically both.

Correct your fstab.

If you want to allow everyone to read the drive, change umask=007 to umask=000 in /etc/fstab on the lines with vfat in them

---

### Post by Nerdriot on 2008-03-24
Thanks guys :)

Here's fdisk -l:

```
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa189a189

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1008     8096728+  83  Linux
/dev/sda2            1009        1133     1004062+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4398    35326903+   7  HPFS/NTFS
/dev/sdb2            4399        4865     3751177+  12  Compaq diagnostics

Disk /dev/sdc: 507 MB, 507322880 bytes
16 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         983      495313+   6  FAT16

```

And, here's fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=32f6c166-266c-4d13-9715-fb1f85a815e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=6010D87310D851A0 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=1B33-0A00  /media/sdb2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=781fafff-0adc-42b2-ad47-ece8d73fb459 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

```

So I should change umask=007 on the sdb1 to 000?

EDIT: Wtf is with the "Compaq Diagnostics" thing there... I'm on a Dell, and the HD with the 2 OS's was from an IBM... oh well.. weird.

---

### Post by kpkeerthi on 2008-03-24
[http://ubuntuforums.org/showpost.php?p=4575372&postcount=3](http://ubuntuforums.org/showpost.php?p=4575372&postcount=3)

---

### Post by keratos on 2008-03-24
> **Nerdriot said:**
> Thanks guys :)

Here's fdisk -l:

```
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa189a189

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1008     8096728+  83  Linux
/dev/sda2            1009        1133     1004062+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4398    35326903+   7  HPFS/NTFS
/dev/sdb2            4399        4865     3751177+  12  Compaq diagnostics

Disk /dev/sdc: 507 MB, 507322880 bytes
16 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         983      495313+   6  FAT16

```

And, here's fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=32f6c166-266c-4d13-9715-fb1f85a815e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=6010D87310D851A0 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb2
UUID=1B33-0A00  /media/sdb2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=781fafff-0adc-42b2-ad47-ece8d73fb459 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

```

So I should change umask=007 on the sdb1 to 000?

EDIT: Wtf is with the "Compaq Diagnostics" thing there... I'm on a Dell, and the HD with the 2 OS's was from an IBM... oh well.. weird.


Either
1. Provide your user ID and GID as options. 
2. Remove the GID option and change umask to 000
3. Ad-hoc mount as root.
4. Note ntfs can only be read from, not written to, unless you have the ntfs3g kernel module thing (cant remember the actual name)

---

### Post by Nerdriot on 2008-03-24
> **keratos said:**
> Either
1. Provide your user ID and GID as options. 
2. Remove the GID option and change umask to 000
3. Ad-hoc mount as root.
4. Note ntfs can only be read from, not written to, unless you have the ntfs3g kernel module thing (cant remember the actual name)

Well, I removed the GID from sdb1 & sdb2. Then, changed the umask to 000. So far, nothing...

This sucks :(

Since it's the drive that has my Ubuntu partition, it doesn't seem logical that I could unmount, and mount again as root. Besides, I thought it was already mounted as root... I'm so confused, lol...

Anyway, thanks for the help... I'm sure this has got to be a human error... I just wish I knew what that error was.

---

### Post by Nerdriot on 2008-03-24
> **kpkeerthi said:**
> [http://ubuntuforums.org/showpost.php?p=4575372&postcount=3](http://ubuntuforums.org/showpost.php?p=4575372&postcount=3)

I did attempt this, but I apparently made some mistake. It's giving me a message about "/dev/hdb1 not existing", when I created it... <sigh>

I hate being a noob.

---

### Post by keratos on 2008-03-24
> **Nerdriot said:**
> Hello,

Ok, so I have 2 HDs, and one has Windows XP (soon to be removed), and Ubuntu 7.10 on it, and the other has extra stuff.

The problem is, when I boot up in Ubuntu, I can view the "extras" HD, but I can't view the stuff on the Windows XP partition, on the same HD as Ubuntu....
[/CODE]

Now you are confusing US.

According to your posts above, your linux install IS NOT on the same HDD as XP

This is my interpretation of your data:

1. sda1 is your Linux install.
2  sda2 is the swap for linux
(no other partitions on this drive!!!!!! No XP!)
3. sdb1 is your XP partition.
4. sdb2 is the compaq crap.
(no linux partition on this disk!!!!)
5. sdc1 is a small fat partition (perhaps data??)

you can only READ from NTFS partitons if you do not have the ntfs3g kernel support, which i doubt you will.

So, you've totally confused me.

Maybe you should start again, and provide consistent information because I can help you no more unless we know what the setup/issue is.

---

### Post by Nerdriot on 2008-03-24
> **keratos said:**
> Now you are confusing US.

According to your posts above, your linux install IS NOT on the same HDD as XP

This is my interpretation of your data:

1. sda1 is your Linux install.
2  sda2 is the swap for linux
(no other partitions on this drive!!!!!! No XP!)
3. sdb1 is your XP partition.
4. sdb2 is the compaq crap.
(no linux partition on this disk!!!!)
5. sdc1 is a small fat partition (perhaps data??)

you can only READ from NTFS partitons if you do not have the ntfs3g kernel support, which i doubt you will.

So, you've totally confused me.

Maybe you should start again, and provide consistent information because I can help you no more unless we know what the setup/issue is.

Incorrect... :)

This is what I originally said:

"Ok, so I have 2 HDs, and one has Windows XP (soon to be removed), and Ubuntu 7.10 on it, and the other has extra stuff."

2 HDs. One, has Windows XP AND Ubuntu 7.10. The other has "extra stuff".

I set up a partition on the first HD; the one that has Windows on it. My initial goal was to install Ubuntu on it, then read the drive and remove XP from it, once I made sure that 3d, etc., was working fine.

However, I am unable to view the remainder of the hd. Instead, it shows the SECOND hd as sdb1, and sdb2 is some random disk labeled "IMB_Service". I have no idea what that's about.

My confusion is worse than yours. I'm confused as to why I'm unable to view the rest of the HD. I know it has things on it. It's only letting me view the Ubuntu partition, though, and not the XP partition.

Here, I'll post my "mount" again. Maybe that'll clear things up...

```
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb2 on /media/sdb2 type vfat (rw,utf8,umask=000)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

No disrespect, but I think your confusion lies in misreading what I said. You don't HAVE to help; keep that in mind.

---

### Post by Nerdriot on 2008-03-24
Update:

As I was going through GParted, and apparently, Ubuntu and Windows XP are both on sda, and the "extras", which is the second hd, is sdb. It's saying that the Windows portion of the partition is "unallocated". But regardless, it's not letting me view the contents of that partition.

It is, however, letting me view all of the sdb hd, so I can't complain about that.

---

### Post by Nerdriot on 2008-03-25
Screw it. Windows was borked during the partitioning anyhow (wtf), so I'm giving the remainder of the hd to Ubuntu.

Marking the thread as "solved", though I'm at a loss.

---

### Post by Moop on 2008-03-25
You can unmount a partition on the same hdd as a mounted partition. I think there was some confusion about that. Anyway...
Try this tutorial and see if it helps mounting windows. 
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by keratos on 2008-03-25
Well, I was confused by your posts.

Lets start again and take away any specifics, and instead empower you with the knowledg in laymen terms, no disrespect intended if I'm teaching you to suck eggs, so far as mounting and partitions are concerned...

The first thing to remember is that you cannot unmount a linux "root" partition. Now in the sense of partitions, "root" has nothing, nothing to do with the user "root". In linux think as root as the "top ancestor" or "the primary reference". In the context of paritions, root means the first partition holding the primary filesystem aka "/" or "root fs".  In the context of users, root is the "top" user, the system admin with all power.

Now, you cannot unmount a root fs. This is because the O/S you are running is "working" from the root fs."Hanging off" this root fs are your user accounts, all your executables, your linux bootable images, your system configs, etc.etc. Taking the root fs away or "unmounting" it would be akin to taking a Windows XP out of the CDROM during an install and then thinking it would be capable of continuing the install. Clearly not, you would (and do) get the "Please insert CD ..." message. In linux, you just cannot do it. So this explains why Gparted (and indeed any other partition tool) will not allow you to do very much with the root fs.

What you would have to do here is boot a live CD and use the Gparted tool on the live CD to modify the partitions on your hard disk which clearly would not be mounted (or more importantly if it is , permitted to be unmounted because you are running from a root fs on CD and NOT on a hard disk).


Moving to specifics..

What I did not account for in my previous requests was for the possibility that you had unused or unmountable partitions on your disks. So, what I should, and would now request, is results from the commands:
```

parted /dev/sda print
parted /dev/sdb print
blkid

```

I wouldnt give up just yet, this is simple to resolve and besides...

Us humans are infinitely more superior than a computer thus the ego and balance must be maintained. Dont let them beat you !!! 
:lolflag:

post the output from the above commands and in the meantime you may wish to boot from a liveCD to do the partitioning of sda. Note that some kernels (versions) adopt different nomclementures for disks, thus one distro or even the same distro with different kernels, will use sdaX, sdbX and so on whereas another will use hdaX hdbX etc. This is due to some kernels using different disk device drivers (modules) like the IDE module or the LIBSATA modules, dont worry, you should be able to identify them by the size and name (labels)

Good luck.

---

### Post by Nerdriot on 2008-03-25
> **keratos said:**
> Well, I was confused by your posts.

Lets start again and take away any specifics, and instead empower you with the knowledg in laymen terms, no disrespect intended if I'm teaching you to suck eggs, so far as mounting and partitions are concerned...

The first thing to remember is that you cannot unmount a linux "root" partition. Now in the sense of partitions, "root" has nothing, nothing to do with the user "root". In linux think as root as the "top ancestor" or "the primary reference". In the context of paritions, root means the first partition holding the primary filesystem aka "/" or "root fs".  In the context of users, root is the "top" user, the system admin with all power.

Now, you cannot unmount a root fs. This is because the O/S you are running is "working" from the root fs."Hanging off" this root fs are your user accounts, all your executables, your linux bootable images, your system configs, etc.etc. Taking the root fs away or "unmounting" it would be akin to taking a Windows XP out of the CDROM during an install and then thinking it would be capable of continuing the install. Clearly not, you would (and do) get the "Please insert CD ..." message. In linux, you just cannot do it. So this explains why Gparted (and indeed any other partition tool) will not allow you to do very much with the root fs.

What you would have to do here is boot a live CD and use the Gparted tool on the live CD to modify the partitions on your hard disk which clearly would not be mounted (or more importantly if it is , permitted to be unmounted because you are running from a root fs on CD and NOT on a hard disk).


Moving to specifics..

What I did not account for in my previous requests was for the possibility that you had unused or unmountable partitions on your disks. So, what I should, and would now request, is results from the commands:
```

parted /dev/sda print
parted /dev/sdb print
blkid

```

I wouldnt give up just yet, this is simple to resolve and besides...

Us humans are infinitely more superior than a computer thus the ego and balance must be maintained. Dont let them beat you !!! 
:lolflag:

post the output from the above commands and in the meantime you may wish to boot from a liveCD to do the partitioning of sda. Note that some kernels (versions) adopt different nomclementures for disks, thus one distro or even the same distro with different kernels, will use sdaX, sdbX and so on whereas another will use hdaX hdbX etc. This is due to some kernels using different disk device drivers (modules) like the IDE module or the LIBSATA modules, dont worry, you should be able to identify them by the size and name (labels)

Good luck.

Thank you :D And I'll definitely keep this in mind "the next time", and I KNOW there will be a next time, since I'm prone to making mistakes, hah... ;)

Thank you for your patience with me. I'm still a noob (Linux users since Jan.), but I've learned that the Ubuntu community in particular is VERY patient and helpful. :)

Edit: Last night, before I went to sleep, I went ahead and formatted the entire HD, removing Windows XP altogether. So now, Ubuntu has the whole hd (and I'm glad it does). ;) A complete switch to Ubuntu feels niiiiiiiiiiiiiiiiiice... :D

---

### Post by keratos on 2008-03-25
okay fine.

I have been using Linux for some 18years and never wain at the *FREE* support on offer. 

Linux has come a long long way and is truly a contester now against the "other" operating system.

I hope you find the ubuntu community welcoming and remember ...

always, always come here first and have patience and allow us to assist.

take care.

---

