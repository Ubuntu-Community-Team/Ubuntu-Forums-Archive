---
title: "/home says full but it's not"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by taddy_porter on 2007-05-06
After reinstalling to Feisty last night my /home is reporting that it's 100% full. Only problem is that it's a 74gb drive and I've only used about 5gb of it. I look through all the directories with disk usage analyzer and they only add up to the 5gb. What's going?

---

### Post by hyper_ch on 2007-05-06
Please post the output of:

```

sudo fdisk -l

```

---

### Post by laidback on 2007-05-06
Have you deleted lots of files?, they remain in the wastebin until purged, /home will have its own, have a look at /home/.Trash (dot before the word Trash, it's a hidden directory)

---

### Post by taddy_porter on 2007-05-06
.Trash is empty. I did previously use KDE though. I have my /home on a seperate partition.

```
Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdd: 40.9 GB, 40981118976 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1         153     1228941   82  Linux swap / Solaris
/dev/hdd2             154        4982    38788942+  83  Linux

Disk /dev/hde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1       19457   156288321   83  Linux

Disk /dev/hdg: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1       24792   199141708+  83  Linux

```

---

### Post by hyper_ch on 2007-05-06
Sorry, I mean to type:

```

sudo df -l

```

---

### Post by taddy_porter on 2007-05-06
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1       24792   199141708+  83  Linux
taddy@taddy1:~$ sudo df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdd2             38180172   5109020  31131708  15% /
varrun                  517976       112    517864   1% /var/run
varlock                 517976         0    517976   0% /var/lock
procbususb              517976       124    517852   1% /proc/bus/usb
udev                    517976       124    517852   1% /dev
devshm                  517976         0    517976   0% /dev/shm
lrm                     517976     34504    483472   7% /lib/modules/2.6.20-15-386/volatile
/dev/hdc1             76912384  72835040    170340 100% /home
/dev/hdg1            196015808 161664196  24394528  87% /home/taddy/download
/dev/hde1            153834852    192072 145828364   1% /home/taddy/media

```

---

### Post by Herman on 2007-05-06
Hello taddy_porter, 
The above posters are probably right, but I also have these two tips to add for you to try as well.

One quick and easy way to clear some junk out of a jammed file system is to run  the following command, 'sudo apt-get clean', that usually makes a bit of space in a crowded file system pretty quick. ```
sudo apt-get clean
```

I have had it happen to me that the partition is big enough but for some reason the file system inside it is small, so the file system reports itself as being 100% full, which may be true, but the partition is still relatively empty.

The easiest way to fix that is to download the latest version of [GParted -- LiveCD]("http://gparted.sourceforge.net/") and burn it to a disk, boot it, right-click on the partition and click 'check'. One of the things GParted LiveCD will do for you is grow the file system to fill the partition. That should cure your problem if I'm correct in assuming it's the problem I am thinking of.

Regards, Herman  :)

---

### Post by Skrynesaver on 2007-05-06
The filesystem /home (/dev/hdc1) is *nearly* full, When you setup an ext filesystem it reserves 5% for root's use only, this allows you to do things as root in the event that the filesystem is full and you need to tidy up, (a good thing).  you can alter the percentage reseved for root using tune2fs -m <new_percentage> /dev/hdc1

---

### Post by laidback on 2007-05-06
Have you copied a DVD?, when I tried this I filled up the partition, even after I aborted the process the partition still reported as being full; temp files somewhere I guess. Bootable Gparted reported disc as full. Rebooting cured it, I assume that the DVD copy temp files were deleted in the process.

---

### Post by hartz on 2007-05-06
> **taddy_porter said:**
> After reinstalling to Feisty last night my /home is reporting that it's 100% full. Only problem is that it's a 74gb drive and I've only used about 5gb of it. I look through all the directories with disk usage analyzer and they only add up to the 5gb. What's going?

Most likely you deleted files which were open.  Linux will only release the disk blocks once all file handles on a file has been closed.

Rebooting is a sure way to get all file handles closed, but if you could work out what program is holding on that amount of files, shutting it down or killing the process is also going to free the file handles.

Before rebooting, go ahead and just exist any programs as far as possible.  If this doesn't work, give the reboot a try.

---

### Post by Skrynesaver on 2007-05-06
If you wish to keep the system running as hartz3 suggests
```

sudo fuser <file I thought I'd deleted>

```
will return the PID of the process that is using the file descriptor

---

### Post by bashologist on 2007-05-06
sudo du -h --max-depth=1 --all ~

---

### Post by tisk on 2007-05-14
hi, I thought I had exactly the same problem.
I did a disk usage analysis and came to similar conclusions: that my filesystem wasn't full.
However from  my windows partition I found that in my root folder, .trash had collected about 12GB of data! This hadn't shown up in the disk usage scan. This makes me wonder why root is collecting trash from my user trash and why it doesn't show up?

anyway, I thought this might help someone else if they hadn't considered root /.trash

---

### Post by Big_Croc7 on 2007-05-14
Hi, I have exactly the same problem - mine arose like this:
/home is almost full - genuinely full, of real files, and I keep getting warnings saying '/home is 95% full' etc.
So... I expand the partition by 50%... on the next bootup, '/home is 95% full' appears; properites reports it as the new size, but everything in it only adds up to the old size.
:confused:
Sorry this dosen't help answer the question though... still haven't solved it!

---

