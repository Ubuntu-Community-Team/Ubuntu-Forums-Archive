---
title: "Cannot access /home after resizing"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Proshka on 2007-11-28
Hi,

I resized my /home partition and although I can log in I do not see any of the files I have in there. 

```


kid@Minerva:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=d5a11df1-08d6-42c1-ab28-b5a80f1289f9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=685b2913-d626-4434-a060-84c803d14b2f /home           ext3    defaults        0       2
# /dev/hda1
UUID=D25887AE58878FC1 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=162f3491-8f8d-42c1-a49e-29c12dd3c797 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

Please help!

---

### Post by Nano Geek on 2007-11-28
It's possible that you deleted the contents of your home folder, but I don't think that you would be able to login if that were the case. 

Can you check and see if that partition has any data in it?

---

### Post by Proshka on 2007-11-28
> **asjdfwejqrfjcvm msz34rq33 said:**
> It's possible that you deleted the contents of your home folder, but I don't think that you would be able to login if that were the case. 

Can you check and see if that partition has any data in it?

You are right, I just resized the partition without deleting anything. Now I remember having an error message when resizing the /home (corrupted volume perhaps?). The partition has 31,9 GB of data (according to the disk analyzer).

---

### Post by Proshka on 2007-11-28
I checked out Gparted and the partition is also there. It seems that after the resizing some of the volume is completely hidden and the remaining space (6 GB) is totally accessible.

---

### Post by Nano Geek on 2007-11-28
That's strange. I'm not really sure what to do about that. 
If you made a backup before you started, then you might just want to reformat that partition. Does hitting **CTRL+H** do anything?

---

### Post by Proshka on 2007-11-28
Unfortunately not. I resized partitions before and nothing strange happened. The problem is that I have all my stuff (mainly work) in there. I hoped there might be another chance to solve the problem without having to reformat.

---

### Post by Nano Geek on 2007-11-29
I'm not sure if it's possible to extract your data from that drive. 
Maybe someone with more knowledge about the issue could help?

---

### Post by Proshka on 2007-11-29
A tout seigneur, tout honneur... 
Even though I wanted to get rid of Window$ completely, I kept it because of the well known issue with Lexmark scanners without Linux support. Now it happens that XP helped me to recover all my files. I have Ext2IFS installed and to my surprise I could access all the Linux partition (ext3 filesystem) although it was a total mess. I was lucky enough to find the files I needed the most (work and university) buried in lost+found, all them mixed up with configuration files of all sorts (10 GB). Perhaps this recovering could be done using Ubuntu too but I am a newbie and I was in panic. The solution I got was not bad anyway. Now formatting will not be so painful and of course I will have learned a lesson about making a backup of the /home partition before going to play with GParted. 
Thanks asjdfwejqrfjcvm msz34rq33 for your posts.

---

### Post by mcduck on 2007-11-29
If you resized the home partition it's UUID changed. And your fstab is still trying to mount the partition with the old UUID. Because of this, it can't find your real /home and probably just gives you a new, empty home directory instead.

Run 'blkid' to list UUID's for your partition, and then edit the /etc/fstab-file to use the correct UUID. That should fix your problem.

---

### Post by Nano Geek on 2007-11-29
Thanks mcduck, I didn't know that.

---

### Post by natehatewindows on 2007-11-29
here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=27c96fda-9808-4018-a7cf-737a53434618 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=e0c6a6ab-e798-4e88-91ae-798adb4556f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1       /home    ext3     nodev,nosuid  0  2
/dev/sda3 /media/storage ext3 defaults 0 1

please note that sda1 is my /home....no uuid.....i dont even think you need it. my /home works perfect.

---

### Post by Proshka on 2007-11-29
> **mcduck said:**
> If you resized the home partition it's UUID changed. And your fstab is still trying to mount the partition with the old UUID. Because of this, it can't find your real /home and probably just gives you a new, empty home directory instead.

Run 'blkid' to list UUID's for your partition, and then edit the /etc/fstab-file to use the correct UUID. That should fix your problem.

This is the blkid input:

```
kid@Minerva:~$ blkid
/dev/hda4: UUID="685b2913-d626-4434-a060-84c803d14b2f" SEC_TYPE="ext2" TYPE="ext3" 

```

As to /etc/fstab-file, the editor opens up an empty file. Should I add a line including the above information? If so, what should I write? 
/etc/fstab shows the same UUID:

```

/etc/fstab: static file system information.

<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4
UUID=685b2913-d626-4434-a060-84c803d14b2f /home           ext3    defaults        0       2
```

---

