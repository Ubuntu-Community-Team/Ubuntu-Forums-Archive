---
title: "hard drive question"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Loki*PI on 2008-04-13
Ubuntu is installed on a 80 gig hard drive.  The / mount point, I'm not sure of my terminology here, only sees 16 gig.  I'm running out of room in /.  Is there any way to add gigs to /?  

If I create a new mount point in the unused space how do I assign gigs to it?  

And if I do that how do I get Ubuntu to use it, say if I want to install more software?  

I'd like to try compiling something but I don't have room to download all the dependencies.   

Thanks for any help.

---

### Post by 1/0 on 2008-04-13
I'm not sure I understand you correct and this is something you do not want to mess up so backup!

Ubuntu is installed on a partition that's 16Gb out of 80? Is the rest of the drive partitioned or not? Check:

```
sudo fdisk -l
df -h
```

---

### Post by Loki*PI on 2008-04-13
Yes this was a second drive in an XP installation.  I put Ubuntu on it to try and learn it a bit.  Then the XP drive died, now this the only drive.

Output:

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7837    62950671    7  HPFS/NTFS
/dev/hdb2   *        7838        9644    14514727+  83  Linux
/dev/hdb3            9645        9729      682762+   5  Extended
/dev/hdb5            9645        9729      682731   82  Linux swap / Solaris

ric@Hawk:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb2              14G   10G  3.0G  77% /
varrun                379M   88K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
udev                  379M   72K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   34M  345M   9% /lib/modules/2.6.22-14-generic/volatile

Thanks

---

### Post by 1/0 on 2008-04-13
```
Device Boot Start End Blocks Id System
/dev/hdb1 1 7837 62950671 7 HPFS/NTFS
/dev/hdb2 * 7838 9644 14514727+ 83 Linux
/dev/hdb3 9645 9729 682762+ 5 Extended
/dev/hdb5 9645 9729 682731 82 Linux swap / Solaris
```

```
Filesystem Size Used Avail Use% Mounted on
/dev/hdb2 14G 10G 3.0G 77% /
varrun 379M 88K 379M 1% /var/run
varlock 379M 0 379M 0% /var/lock
udev 379M 72K 379M 1% /dev
devshm 379M 0 379M 0% /dev/shm
lrm 379M 34M 345M 9% /lib/modules/2.6.22-14-generic/volatile
```

Well from what I can tell, there is space left above cylinder 9729. You should be able to create a partition in the unpartitioned space via cfdisk for instance. I don't use gparted but people use it so I guess its got advantages. After that you need to format it (mke2fs -j /dev/hdbX X is the number of the new partition as above. Probably 6.)

Last thing is to make it mount at start. You need to edit fstab for that:

```
sudo nano /etc/fstab
```

And you want to add your partition there and decide where to mount it.  I would suggest as /home. The line should look something like this:

```
/dev/hdbX   /home   ext3   defaults   0   2
```

Now before you mount this partition as /home you will want to empty the old one since its gonna be invincible, once the partition is mounted. You need to mount it as something else.

```
mkdir tempfolderformounting
sudo mount /dev/hdbX tempfolderformounting
```

Now you can use your file browser to move (not copy) everything, including hidden folders, to the tempfolder you created. 

When you have checked that everything is there.

```
sudo umount tempfolderformounting

rmdir tempfolderformounting
```

Restart the computer and you should be fine.

Now IF ITS NOT unpartitioned space you will destroy the content, i.e. everything. IF you misspell when formatting you will delete everything on that partition, so DON'T do a sudo mfe2fs -j /dev/hdb1 because you will DELETE your windows partition. I've hardly slept this night so chances are I could have missed something, just so you know... But if you back it up, you're safe.

---

### Post by 1/0 on 2008-04-13
I just found this guide and it does the whole thing much easier:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

