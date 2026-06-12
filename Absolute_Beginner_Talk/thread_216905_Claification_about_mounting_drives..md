---
title: "Claification about mounting drives."
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-07-16
I am a little confused about mounting drives.
I know what it mean so no explain is needed.
But it seem like there is conflicting information about it. I will explain.

I was looking for help on mounting drives I came appound this page 
[Mount Partions Automatically]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")
In the second paragraph it talks about how this procedure is know automated almost. Or at least this is how I interperted it.
> With the release of Breezy Badger (Ubuntu 5.10), this step should be almost automatic. Until then, however, the instructions provided on this page may be used to mount any needed existing data.

What does it mean? Where is this almost automated mounting of harddrive? I have looked but do not seem to find it.

Or is the article mean the script indicate is the automatic way of doing this?
By the way here is what I want to mount. 
> ed100@ed100-desktop:~$ sudo fdisk -l

Password:


Disk /dev/hda: 
20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   
Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1020     8193118+   b  W95 FAT32
/dev/hda2            1021        2434    11357955    f  W95 Ext'd (LBA)
/dev/hda5            1021        2434    11357923+   b  W95 FAT32

Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1275    10241406    c  W95 FAT32 (LBA)
/dev/hdb2            1276        3877    20900565    f  W95 Ext'd (LBA)
/dev/hdb3   *        3878        4982     8875912+  83  Linux
/dev/hdb5            1276        2550    10241406    b  W95 FAT32
/dev/hdb6            2551        3825    10241406    b  W95 FAT32
/dev/hdb7            3826        3877      417658+  82  Linux swap / Solaris
ed100@ed100-desktop:~$



As you can see I have number of partitions. I would like to be able to have this mounted automattically when I boot into Ubuntu.
I know I can do it manually but if there is an automatic way, I would rather do it that way.

I also came across this article which shows how to modify the [fstab]("https://help.ubuntu.com/community/MountingWindowsPartitions") so the harddrive are mounted at boot up. Or is this what they meant by automate mounting?

Can you see why I am confuse.
So can someone please clarify thing for me.

---

### Post by sas on 2006-07-16
Your partitions should be automatically detected at installation time and added to /etc/fstab

---

### Post by gargoyle on 2006-07-16
> **sas said:**
> Your partitions should be automatically detected at installation time and added to /etc/fstab

Does this mean the are automatically mounted?
Or do I have to mount them?

I have gone to the File manage to see them but they seem to be unaccessible.
If so then I have to modify the fstab, correct?

Also I have checked under the File manager list there
**media**
cdrom 0
cdrom 1
floppy

To me this means they are not mounted.
Just check the fstab and I do not see them as beening mounted.

So I guess this means I have to edit the fstab to get them mounted. Is this correct?

---

### Post by RRS on 2006-07-16
> I also came across this article which shows how to modify the fstab so the harddrive are mounted at boot up. Or is this what they meant by automate mounting?

Yes, I believe that's what you're asking for.

You might also check out [this guide.]("http://www.psychocats.net/ubuntu/mountwindows.php")

It's the same basic instructions but with a  little more complete explanation. The same site also contains a lot of other helpfull information.

---

### Post by gargoyle on 2006-07-17
Just want to close the post with mission accomplished.
I now have my partition all automatically mount on startup.
This was done with the following.
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy  auto    rw,user,noauto  0       0
/dev/hda1 /home/ed100/fat_c vfat iocharset=utf8,umask=000 0 0
/dev/hda5 /home/ed100/fat_d vfat iocharset=utf8,umask=000 0 0
/dev/hdb1 /home/ed100/fat_g vfat iocharset=utf8,umask=000 0 0
/dev/hdb5 /home/ed100/fat_h vfat iocharset=utf8,umask=000 0 0
/dev/hdb6 /home/ed100/fat_i vfat iocharset=utf8,umask=000 0 0


I have one last adjustment and that is to change the floppy to write imediately upon a File save or Save as.
Other then that it work, as you can see each partition has it own  directory and the directories are name to corespond to the WinXp directories.

Thanks for all the replies

---

