---
title: "Repartitioning Ubuntu"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-12
Hi, I installed Edgy on my computer a couple weeks ago (dual boot with XP) and i'm getting the feeling I messed up the partition sizes a bit.  

I wanted to allocate about 20 Gigs for Ubuntu, and I have a 512 Mb Ram.  

I ended up using 988MB for swap and I realize that's probably too much (that's the only partition who's name I know, so please bear with me here).  I have three other partitions, only known to my by 'sda3',  'sda7' and '/'.  

sda3 is 3.3 GB and it's the drive that contains folders with names like bat, src1, src2, src3, src4, src5, img, bin, autoexec.bat and a few more.

sda7 is 10 GB and it's completely empty except for one folder labeled 'lost+found'

And then there's the '/' folder with the root directory in it.  I can't figure out how big that is but it seems like it's probably around 7 Gb and it only has 3.1 Gb free 

Any advice on how to resize those partitions (both, how big they should be and what program I should use) will be greatfluly received

---

### Post by FuturePast on 2007-05-12
You can use Gparted from within a live cd to resize your partitions.

---

### Post by zhinker on 2007-05-12
Thanks, that's half the problem solved.  So anyone know what's a good size to make the partions?

---

### Post by Steven_B on 2007-05-12
988 MB isn't too much for a swap partition.
Type "sudo fdisk -l" in a terminal to see all of your partitions, and where they are mounted.
Type "df" to see how much of each partition is used.

---

### Post by zhinker on 2007-05-12
> **Steven_B said:**
> 988 MB isn't too much for a swap partition.
Type "sudo fdisk -l" in a terminal to see all of your partitions, and where they are mounted.
Type "df" to see how much of each partition is used.

This is what I got:

```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        6738    54066757+   7  HPFS/NTFS
/dev/sda3            9299        9725     3429877+  db  CP/M / CTOS / ...
/dev/sda4            6739        9298    20563200    5  Extended
/dev/sda5            6739        7757     8185086   83  Linux
/dev/sda6            7758        7883     1012063+  82  Linux swap / Solaris
/dev/sda7            7884        9298    11365956   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    c  W95 FAT32 (LBA)
zain@ip68-109-35-131Zain:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5              8056492   4412752   3234488  58% /
varrun                  257308        64    257244   1% /var/run
varlock                 257308         4    257304   1% /var/lock
procbususb               10240       136     10104   2% /proc/bus/usb
udev                     10240       136     10104   2% /dev
devshm                  257308        64    257244   1% /dev/shm
lrm                     257308     18132    239176   8% /lib/modules/2.6.17-11-386/volatile
/dev/sda1                56068      7488     48580  14% /media/sda1
/dev/disk/by-uuid/34DCDB0BDCDAC670
                      54066752  45827868   8238884  85% /media/sda2
/dev/sda3              3423168   3064520    358648  90% /media/sda3
/dev/sda7             11187352    131260  10487796   2% /media/sda7
/dev/hda                600232    600232         0 100% /media/cdrom0
/dev/sdb1            156250144 141902304  14347840  91% /media/HD-HBU2

```

sda2 is my windows partition, and I don't know what the DellUtility partition is for, it was there from the start.  I'm not sure what sda4 and sda5 are, I thought those were the partitions I created and deleted while trying to install Ubuntu.  

Shouldn't they be gone since they obviously don't exist?
:confused:

I have no idea what any of the other partitions are...help?

---

### Post by Steven_B on 2007-05-12
sda1 - I don't know what this is either.  It's really small, so I probably wouldn't worry about it.
sda2 - As you mentioned, this is the Windows partition.
sda3 - I don't know what this is.  "autoexec.bat" sounds like Windows stuff - My best guess is that it is some kind of Windows backup partition.  Do you know if it was there before you installed Ubuntu?
sda4 - This is an extended partition, which means it is a container for other partitions (in this case, sda5, sda6, and sda7)
sda5 - This is your Linux root partition (where / is mounted)
sda6 - Linux swap partition, which is why it doesn't show up from df.
sda7 - As you mentioned, this is empty.

Don't worry about  varrun, varlock, procbususb, udev, devshm or lrm.  As I understand it, these are "imaginary" partitions, which are not on your hard drive.

I would suggest combining sda5 and sda7.  This means moving the swap partition the the beginning or end of the extended partition (it's currently stuck in the middle).  You might run into this issue if your swap partition changes numbers: [http://ubuntuforums.org/showthread.php?t=241703]("http://ubuntuforums.org/showthread.php?t=241703")

Another possibility would be to use sda7 as your /home partition.  All of your files can stay there, and Ubuntu itself would be stay on sda5.  That way, if you ever reinstall Ubuntu, your configuration files don't get wiped out.
The downside to this would be if you needed more than 3 Gb for additional programs, in which case you would have to rearrange the partitions anyway.

---

### Post by zhinker on 2007-05-13
I like the idea of having sda7 as the /home partition.  How do I set it up to be that?

---

### Post by Steven_B on 2007-05-13
First, you have to copy current home folder files onto the new partition.  It's probably best to do this from a live CD.
```
cp -p all /media/??/home/* /media/??/ 
```  Replace "??" with the names the live CD has given to your partitions.
Then rename /home to /oldhome (once the new partition is up and working, you can delete oldhome).  Create a new, empty directory called home.  This will be the mount point for the other partition.

Next, edit /etc/fstab to mount sda7 on /home with "sudo gedit /etc/fstab" (or "sudo gedit /media/??/etc/fstab" if you're still using the live CD).

Find the line with sda7 in it, which should look similar to this:
```
/dev/sda7 -- converted during upgrade to edgy
UUID=ac67ba79-d0f5-4738-95e0-ef3537845d40 /media/sda7 ext3 defaults 0 1
```
It might say something like this instead:
```
/dev/sda7 /media/sda7 ext3 defaults 0 1
```
Just change /media/sda7 to /home, save the file, and reboot.

Just as a warning, this has the potential to break things.  If it does, let us know, and we'll try to help.  As a last resort, you can use the Live CD to restore your files in /home.  Just delete the home folder and rename oldhome to home.

---

### Post by zhinker on 2007-05-13
Hmm...on second thought I think I'll just combine my sda5 and sda7 partitions.  I don't really plan on reinstalling Ubuntu and moving the /home folder seems a tad too complicated and risky.

Thanks anyways though

---

### Post by zhinker on 2007-05-13
Umm, how do I use Gparted?

---

### Post by Steven_B on 2007-05-13
You might want to look here:
[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

---

### Post by jerrylamos on 2007-05-13
Gparted - well, try CD Live, System, Administration, Gnome Partition Editor
If' it's not on CD Live, then do Applications, Add/Remove, search GParted, select, apply.
Start Gparted as on first line.
Top right corner of Gparted should allow switching to different hard drives if you need to.
The partitions are in the middle.
Generally, to re-partition, delete adjacent partitions like your 5, 6, 7.
Then you can create  a new partition, I like 20 gb for Linux however 10 gb will do, select format ext3, mount point /
(I can't go thru these steps right now without messing up my system!)
Swap can be a little over 512 mb for general use, more if you are going to create .iso's (complex!!)
The small Dell partition is where the computer specific support is located including a Microsoft rescue for your operating system.  Leave this partition alone.

Up to 4 partitions can be on the hard drive.  If you want more than 4, then it would be 3 plus 1 extended partition.  The extended partition can then be broken up into two (or more) more.

Cheers, Jerry

---

### Post by LE CHARBON on 2007-05-13
THIS IS MY SPLIT ON A 120G HD. I HAVE A DUAL BOOT XP/UBUNTU

Partition List:
- XP Partition, NTFS, 30 GB, mount /media/hdsomething 

- Ubuntu Partition, Ext3, 15 GB, mount /

- Swap File, Swap, 2.5 GB, doesn't mount like drives

- Home partition, Ext3, ABOUT 70 GB, mount /home

---

