---
title: "Problems with fsck...."
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by trinityj5 on 2007-01-04
Hi there :) 

Happy New Year to all!!

Right, here is my problem... I am running a dual boot with Windows XP Pro amd Ubuntu 6.06. I have two hdd's on my system. One is my orginal Windows hdd with XP Pro on it and the other one is split into some partitons, my fdisk -l reads as follows...

```
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
16 heads, 63 sectors/track, 581463 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2      481648   242750088    f  W95 Ext'd (LBA)
/dev/hdb2          579051      581463     1216152   82  Linux swap / Solaris
/dev/hdb3   *      481649      579050    49090608   83  Linux
/dev/hdb5               2      203176   102400168+   b  W95 FAT32
/dev/hdb6          203177      406351   102400168+   b  W95 FAT32
/dev/hdb7          406352      477462    35839912+  83  Linux
/dev/hdb8          477463      481648     2109712+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

My problem is that the two fat32 partitions on hdb have become unradable by windows, it says that the drive is not formatted, so I am assuming that somehow they have lost their filesystem... I don't know why, or how... :( 

As you can imagine I want the data back that was on the fat32 partitions, I ran a data recovery prog on windows and that confirmed all my data was there, but before running out and buying a new hdd to copy all the data to, I wanted to see if I could restore the filsystem and save the bother/money. My friend, running FC4, said that I could type```
fsck.msdos /dev/hdb5
``` into terminal and it would restore the filesystem, however when ever I try this I get this error:

```

john@Trinity:~$ sudo fsck.msdos /dev/hdb5
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Seek to 2203318222335:Invalid argument

```

I have no idea what this means, and I have hit a bit of a brick wall, I just wondered if any of you terribly clever people could point me in the right direction!!


Hope this is in the right place!!


John :) :-k

---

### Post by raul_ on 2007-01-04
Why the msdos? I thought
```

fsck device

```

would do it

---

### Post by trinityj5 on 2007-01-05
Well I was under the impression that it needed to be .msdos because it was a windows filesytem..? Surely doing ```
fsck.device
``` would check the entire device? I don't think this is neccesary as linux is working perfectly and it is on the same drive as the two malfunctioning fat32 partitions?


What do you think? Obvioulsy I am almost certainly wrong.... feel free to correct me!!


John

---

### Post by raul_ on 2007-01-05
If you want to check hdb5 just do

```

fsck /dev/hdb5

```

no periods ( . ) i'm pretty sure that'll work

---

### Post by goatflyer on 2007-01-05
I hate to tell you this but your partition table for /dev/hdb is majorly broken.

Specifically, the first partition /dev/hdb1 overlaps (includes/eats/mangles) over partitions 5 through 8.  The only partitions which look 'safe' are hdb2 and hdb3.

Don't attempt to make further 'repairs' right now, it will only mangleover worse. Before you lose any further data, back up what you can.

What is in /etc/fstab?

---

### Post by trinityj5 on 2007-01-05
Hi there, thank you both for getting back to me :) Goatflyer, my etc/fstab reads:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I have no idea what that all means, lol, I guess you do though! :)

One thing I should pont out is that there are two installations of linux on hdb, the first one is/was FC4, which I then overwrote with Ubuntu, I guess that is where the crossover partitions are coming from?

Raul_, I haven't had a chance to try out that command yet, as goatflyer's post kinda scared me!! so I have left it as it is for the second, thanks for your reply though.

 Anyone got any futher ideas? 


Thanks again for all of everyones help!!


John

---

### Post by trinityj5 on 2007-01-06
Hi people, anyone had any further ideas on this? Also, does anyone have any suggestions on data recovery programs?


Thanks 


John :)  ](*,)

---

### Post by bulldog on 2007-01-06
Boot into ubuntu and mount the fat32 partitions.
See if there's data on it and if so copy it to another place.

---

### Post by goatflyer on 2007-01-11
Ok, at least your /etc/fstab is not trying to use the corrupt partitions.


Let's try to peek what if anything is on your partitions 5 and 6

First create a directory owned by root:
```

sudo mkdir /myhd

```

Then try to mount the /dev/hdb5 partition
```

sudo mount -t vfat /dev/hdb5 /myhd

```

If this gave no errors, try:

```

ls /myhd

```

and see if it looks like windows files to you.

Then umount it and try mounting and looking at /dev/hdb6
```

sudo umount /dev/hdb5
sudo mount -t vfat /dev/hdb6 /myhd
ls /myhd

```

Any windows files there either?  Lastly:

```

sudo umount /dev/hdb5
sudo rmdir /myhd

```

to clean up.

---

### Post by trinityj5 on 2007-01-12
Hi there :) Thanks to everyone for getting back to me. I am sorry I haven't been replying, Manic at work. Right so, goatflyer, thanks for running through the code needed for mounting filesystems, was totally unsure and was about post to ask for help when you beat me to it!!

So, after creating a directory called /myhd, I tried:
```
sudo mount -t vfat /dev/hdb5 /myhd
```

However it returned:
```
john@Trinity:~$ sudo mount -t vfat /dev/hdb5 /myhd
mount: wrong fs type, bad option, bad superblock on /dev/hdb5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

What does this mean?! I am guessing it is not good?! I would try the syslog suggestiong and post that up here, but not sure how to get it...? This was also the result when trying it for hdb6...

Any further help would be massively appreciated :)

Thanks very much indeed for all the help offered so far!



John

---

### Post by trinityj5 on 2007-01-13
Any one got any thoughts on this at all?

All help welcomed!!


John:) ](*,)

---

### Post by trinityj5 on 2007-01-17
Hi there people :) Just wondered if anyone had any more thoughts on this? :)


John

---

