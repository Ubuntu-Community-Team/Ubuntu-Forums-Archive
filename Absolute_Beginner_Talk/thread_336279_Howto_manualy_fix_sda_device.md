---
title: "Howto manualy fix sda device"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2007-01-11
Hello,
i just followed a user tip on howto clean a partition.
See here [http://ubuntuforums.org/showthread.php?t=336228](http://ubuntuforums.org/showthread.php?t=336228)

All went ok but now ubuntu is unable to mount the device.

> Log of fsck -C -R -A -a 
Thu Jan 11 18:53:20 2007

fsck 1.39 (29-May-2006)
/dev/sda2: clean, 11/272544 files, 25763/544201 blocks
fsck.ext3: Unable to resolve 'UUID=529b09ba-0750-4dde-baed-19c0fedd5eae'
/dev/sda7: clean, 18/1661376 files, 2270026/3321430 blocks
fsck died with exit status 8

Thu Jan 11 18:53:20 2007

Any idea how to fix this?
The console says it needs to be done manualy.

I know of the mount points, but they dont changed as i just formated the device.
I have no idea where to start ...Can someone help me please? 

Thanks

---

### Post by shareMenaPeace on 2007-01-11
I can mount the device manualy, please can someone let me know how i can edit the boot mount procedure to fix the fsck error?

Thank you for any hint

---

### Post by shareMenaPeace on 2007-01-11
Looks like i can mount everything accept the formated partition.

---

### Post by taurus on 2007-01-11
What's the output of this command and your /etc/fstab as well?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by shareMenaPeace on 2007-01-11
Here
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2811    22579326   83  Linux
/dev/sda2           14323       14593     2176807+  83  Linux
/dev/sda3            2812       14322    92462107+   f  W95 Ext'd (LBA)
/dev/sda5            2812       11165    67103473+   7  HPFS/NTFS
/dev/sda6           12820       14240    11414151   83  Linux
/dev/sda7           11166       12819    13285723+  83  Linux
/dev/sda8           14241       14322      658633+  82  Linux swap / Solaris


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d888bc1e-8e9f-4efa-add0-85d0d8137994 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=df4c5bb8-9fe5-4556-8a40-d415b6624e19 /media/sda2     ext3    defaults        0       2
# /dev/sda5
UUID=12E4E1EE2BA17CA9 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=529b09ba-0750-4dde-baed-19c0fedd5eae /media/sda6     ext3    defaults        0       2
# /dev/sda7
UUID=a68b0c44-95c3-4861-a503-ac5c72f058fe /media/sda7     ext3    defaults        0       2
# /dev/sda8
UUID=ed959b00-5b45-44cd-8293-e084bd35199f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2007-01-11
I would edit /etc/fstab and change this line

```
UUID=12E4E1EE2BA17CA9 /media/sda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```

to this.

```
/dev/sda5   /media/sda5   ntfs   defaults,nls=utf8,umask=007,gid=46  0  1
```
Then, reboot and see if /dev/sda5 is mounted to /media/sda5 at all (with /etc/fstab).

---

### Post by shareMenaPeace on 2007-01-11
I made  a backup and first tried sda6 :P
Which mounted and booted without a problem, accept sda6.

Than i used teh backup and modified sda5 accordingly but now sda5 and sda6 are missing -- not mounted.

I cant mount sda6 manualy.... and thx for showing me where and howto fix this.

Any more ideas for sda6?

---

### Post by shareMenaPeace on 2007-01-11
Maded a failure with the backup, fixed now.
When i do accordingly to your info nothing changes - still error.

When i alter sda6 -- removing the UUID it boots without a glitch, but without sda6.

Would it makes sense to re format again, but with ext2?
Could i merge EXT3 with NTFS - would data stay intact?

---

### Post by shareMenaPeace on 2007-01-11
> **taurus said:**
> 
Then, reboot and see if /dev/sda5 is mounted to /media/sda5 at all (with /etc/fstab).
When i alter sda6, sda5 is mounted.

---

### Post by taurus on 2007-01-11
> **shareMenaPeace said:**
> When i alter sda6, sda5 is mounted.

What do you mean by alter /dev/sda6?  Personally, I replace all the UUID in /etc/fstab to their actual device name like /dev/sdaX.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
/dev/sda1  / ext3 defaults,errors=remount-ro 0 1
# /dev/sda2
/dev/sda2  /media/sda2 ext3 defaults 0 2
# /dev/sda5
/dev/sda5  /media/sda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda6
/dev/sda6  /media/sda6 ext3 defaults 0 2
# /dev/sda7
/dev/sda7  /media/sda7 ext3 defaults 0 2
# /dev/sda8
/dev/sda8  none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0 

```

---

### Post by shareMenaPeace on 2007-01-11
Well i meant with alter sda6, the removal of sda6 UUID.

Anyway i cant logical replicate this but your fstab hack you quoted above is working very well!

Thank you and the community!

I had a really stressful day and basicly what i was doing was to transfer some files from a ftp which made me aware of a full device, which than i learned here can be fixed with gparted and on ...finally this story is over and i learned something!

Anyway i will now remove the last pieces of junk window (extended partition and ntfs) from my system! 

Cheers

---

### Post by taurus on 2007-01-11
Remember, every time you resize or format your harddrive using gparted, the UUID would change so that's why it's a good idea to go back to the /dev/sdaX thing.

---

### Post by shareMenaPeace on 2007-01-11
You mean to get rid of the UUID in first place?

Anyway was able to delete the extended partition and create new primary partitions now and a swap. Created also the /media/sdaX accordingly.

When i first started i had a failure in the fstab which lead to a superblock bug - a search turned out this is a common problem.

Thx

---

### Post by steve.horsley on 2007-01-11
Edgy has started using UUID=??? instead of /dev/??? in fstab. Fortunately, the installer stil puts a commented /dev line immediately above the UUID= line. The UUID= number is a magic number that is written to a partition when it is formatted. The idea is that you can move the hard disk (e.g. so hda1 becomes hda3) and the partitions will still be identified and mount to the right place. The disadvantage is twofold: Firstly, reformatting a partition changes the UUID so the partition is not mounted at all, and the OS bitches about the old partition it can't find any more. Secondly, the rather excellent fstab configuration GUI program **pysdm** doesn't yet work with UUID numbers, so that doesn't work. My advice is to change fstab back to using /dev notation and install pysdm (shows up as Administration->Storage Device Manager).

---

