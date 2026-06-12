---
title: "fsck always runs at startup"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Lord DarkPat on 2008-01-10
Everytime I boot, the bootsplash freezes at 1/4 the bar, then starts fcsk &dosfsck. Its been happenning since I installed it, but didn't bother at the time. It takes about 7mins to start now

---

### Post by barbedsaber on 2008-01-10
fsck is a disk check thin that linux uses to check the disk for errors, it is not suppused to run every boot, only every 30 boots, you may need to disable it, dont know how tho.

---

### Post by kd7swh on 2008-01-10
related question: is there anyway to ask fsck to warn you when you are on your 29th boot without a scan? I would like to have a warning because it sucks when you boot up your laptop in the classroom or lecture hall and you have no time \ battery life to spare.

---

### Post by Paqman on 2008-01-10
[HowTo: Change disk checking/fsck at boot frequency](http://ubuntuforums.org/showthread.php?t=300477)

---

### Post by Herman on 2008-01-10
I wonder what's wrong? If it runs at every start up it's trying to tell you something. Normally it will run the check and then be quiet for another 30 or so boots.

Is there and error message at all?

You can run a more powerful file system check from GParted Partition Editor in your Ubuntu Live CD. 
You just boot your Ubuntu Live CD and open GParted Partition Editor, I think it's in 'System'-->'Administration', and it should be there somewhere.
In GParted you just right-click on the partition to be checked and click 'check' from the right-click menu.
Then you cilck the 'Apply' button on your toolbar, then apply again in the confirmation window.
A reciprocating bar will show up for a few minutes to let you know something in happening and to wait.
When it finished you can click on the triangular expansion buttons for a report on what was done. 

The regular file system check that's done at startup is only an 'fsck' type, which is really good. Fsck isn't a file system check program itself though, it's more like a file system checker manager, it picks out the right program and tells the file system checking to run a generic check. 
With GParted, you are pointing out a specific file system, and GParted can do a more specific  and therefore more effective check for you. 
That should clear your problem.

If it doesn't clear the problem, then we might need to look a bit deeper.

It's always a good idea to run a file system check, that will reset your counter in your superblock for you too.

Regards, Herman :)

---

### Post by LeighT on 2008-01-12
> **kd7swh said:**
> related question: is there anyway to ask fsck to warn you when you are on your 29th boot without a scan? I would like to have a warning because it sucks when you boot up your laptop in the classroom or lecture hall and you have no time \ battery life to spare.

There is a program called "Bonager Boot Scan Manager" in the repositories that does just that.:)

---

### Post by mcduck on 2008-01-12
> **Paqman said:**
> [HowTo: Change disk checking/fsck at boot frequency](http://ubuntuforums.org/showthread.php?t=300477)

That only works with Ext2 and Ext3 partitions.

Anyway, every case where I've seen fsck running on every boot the problem has been that /etc/fstab has been configured to run fsck on FAT or NTFS partitions, which are not able to store data about the last time when they were checked.

To fix that, edit those partition's entries in /etc/fstab and change the last number to 0.  (run 'gksudo gedit /etc/fstab' to open the file for editing)

For example change entry like like this:
```
# /dev/sda1
UUID=9877-489A  /media/sda1     vfat    noauto,defaults,utf8,umask=007,gid=46 0       1
```
..into this:
```
# /dev/sda1
UUID=9877-489A  /media/sda1     vfat    noauto,defaults,utf8,umask=007,gid=46 0       0
```
(your entries will be very different from mine, ignore that and just change the last number, nothing else.)

The last number tells if fsck should check the partition, and in which order they should be checked. '1' should be used for root partition, and only for it. For other partitions you can use '2' to check them after root, or '0' to not check that partition.

---

