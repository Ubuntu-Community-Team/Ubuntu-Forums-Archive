---
title: "creating a new partition for dual boot"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by fnordportland on 2006-10-24
how do i create a new partition?im trying to set up a dual boot so i can run windows :( is there a easyer way than creating a new partition? i tried useing gpart but it dosent give me the option to create a new part.

---

### Post by CatKiller on 2006-10-24
You need to have unallocated space to make a partition in, and you can't modify a partition that's mounted.

---

### Post by ReaderRat on 2006-10-24
How is the HD partitioned now? If you don't know, run this code in Terminal and post the output here
```
cat /etc/fstab
```

---

### Post by fnordportland on 2006-10-24
<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
root@root-laptop:/home/eric#


i have no unpartitioned space,so this means im screwed right?no way to install windows?

---

### Post by ReaderRat on 2006-10-24
And would you run & paste:
```
df -h
```

---

### Post by fnordportland on 2006-10-24
root@root-laptop:/home/eric# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              55G   19G   34G  36% /
varrun                 93M  120K   93M   1% /var/run
varlock                93M  4.0K   93M   1% /var/lock
udev                   93M  112K   93M   1% /dev
devshm                 93M     0   93M   0% /dev/shm
lrm                    93M   19M   75M  20% /lib/modules/2.6.15-27-386/volatile
root@root-laptop:/home/eric#

i dont like that word volatile whats up with that?thats my kernal right?

---

### Post by ReaderRat on 2006-10-24
For Your Information. 
You cannot partition a drive that is in use, like the one you are running Ubuntu on. You have to use a LiveCD of Ubuntu OR [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/download.php) in order to mess with the partitions on your HDD. Also, when you install Windoze, it's going to write over the GRUB bootloader from Ubuntu and you willmot be able to get to Ubuntu. Here is something that may help; **[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)**

---

### Post by ReaderRat on 2006-10-24
If you have not had to do a lots of configuring in Ubuntu, I would suggest just wiping the disk and reinstalling both OS's from scratch, BUT Install Windoze First.

---

### Post by fnordportland on 2006-10-24
not really too too much enuff that it would be anoying,the maine thing is 15 gigs of downloaded songs/movies/books that i dont want to lose/take froever and 20 black cds i dont have to back up

---

### Post by CatKiller on 2006-10-24
The easiest way is to stick in a second hard disk. I think it was gn2 that made quite a nice howto recently. That way, either install can break spectacularly without affecting the other in any way. Which is nice.

Otherwise, you can resize your existing partitions to make some space. Things to bear in mind are that older versions of Windows will only boot from a Primary partition, Ubuntu can read and write FAT32 but only read NTFS, and Windows will overwrite the Master Boot Record where GRUB resides. You'll need to do this from a live cd environment, since otherwise you can't manipulate the partitions on your drive.

Read the link that ReaderRat supplied for how to patch up your MBR after Windows has stuck its bootloader in it.

---

### Post by fnordportland on 2006-10-24
im just going to throw the live cd in and see what hapenns if i figure it out without breacking anything cool,if not ow well.

---

