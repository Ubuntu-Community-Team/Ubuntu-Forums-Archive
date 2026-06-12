---
title: "Ideal Partition Space"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by KarmaKing on 2006-05-16
Hello all,

I am still far behind in regards to overall computer hardware specs running my system with only a 20GB HD.  I use alot of space on it already and want to know how much space would be ideal to run Ubunto live?  I know the recommended minimum is 2 GB, but is more needed? ANd for what?  I don't want to short change my first experience with linux by not giving ample space and I don't want to alter my XP set up too much either...
I have close to 5-8 GB free space, give or take a GB:p 
Thanks in Advance,

KK

---

### Post by Sef on 2006-05-16
> want to know how much space would be ideal to run Ubunto live?

Ubuntu Live is a Live CD.  If you want to use it, it will run off of your harddrive.  If you want to install Ubuntu, then you should have at least 8 GB.

Questions:

1) Are there files or programs that you could delete off of your XP?  

2) Do you want to share files between XP and Ubuntu?

3) Have you ever installed an operating system before?

check out the Illustrated Dual Boot Site:

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

4) What do you use your computer for?  Just basics: Email, web surfing, and writing or other?

5) Do you have any more questions for us?

---

### Post by KarmaKing on 2006-05-16
> 1) Are there files or programs that you could delete off of your XP?

2) Do you want to share files between XP and Ubuntu?

3) Have you ever installed an operating system before?

check out the Illustrated Dual Boot Site:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

4) What do you use your computer for? Just basics: Email, web surfing, and writing or other?

5) Do you have any more questions for us?

Thanks for the quick reply Sef.

answers to your questions.

1. Yes
2. Yes
3. Yes, but not a linux.  I think a large percentage of Windows users are pretty good at installs:mrgreen: 
4. I do use a range of windows based programs alot. (Adobe, Word, Winamp, the occasional video game, ect..) I guess my machine is more of a entertainment center for myself including videos of all different formats.  I do a quite a bit of downloading since I am far from home and have limited local access to movies, TV, radio, ect...

5.  Oh my friend, do please remember my name and avatar pic.  I am going to be here for a while:-D 

kk

---

### Post by Sef on 2006-05-16
If you could have another hard drive installed that would be best since you don't have a lot of room.  

> 
Quote:
1) Are there files or programs that you could delete off of your XP?

2) Do you want to share files between XP and Ubuntu?

3) Have you ever installed an operating system before?

check out the Illustrated Dual Boot Site:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

4) What do you use your computer for? Just basics: Email, web surfing, and writing or other?

5) Do you have any more questions for us?

Thanks for the quick reply Sef.

answers to your questions.

1. Yes
2. Yes
3. Yes, but not a linux. I think a large percentage of Windows users are pretty good at installs
4. I do use a range of windows based programs alot. (Adobe, Word, Winamp, the occasional video game, ect..) I guess my machine is more of a entertainment center for myself including videos of all different formats. I do a quite a bit of downloading since I am far from home and have limited local access to movies, TV, radio, ect...

5. Oh my friend, do please remember my name and avatar pic. I am going to be here for a while



1) Delete what you can to give yourself more space.  

2) To share files, you will need either a FAT32, ext2 or ext3 partition.

3) This site has a lot of good advice and help with dual booting. [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

4) I use Ubuntu as my entertainment center now.  My XP had an unfortunate case of bloatitis, so Dr. GParted decided to delete it out of its misery.  

5) Happy to have you around.  Drop by with your questions anytime. :D

As for the partitions, post how much space you have after you delete what you can, then either I or someone else will make some recommendations.

---

### Post by az on 2006-05-16
[QUOTE=KarmaKing]Hello all,

I am still far behind in regards to overall computer hardware specs running my system with only a 20GB HD.  I use alot of space on it already and want to know how much space would be ideal to run Ubunto live?  I know the recommended minimum is 2 GB, but is more needed? ANd for what?  I don't want to short change my first experience with linux by not giving ample space and I don't want to alter my XP set up too much either...
I have close to 5-8 GB free space, give or take a GB:p 
Thanks in Advance,

KK[/QUOTE]

Depending on what you do with your computer, you may be fine with just three gigs of space for ubuntu.  It really depends.  I think 8 gigs is a little much for a minimum requirement, though....

---

### Post by KarmaKing on 2006-05-20
thanks all for the help.  The drive is partitioned.  I gave windows 10GB, Ubuntu 4, and I left 6GB for sharing.  I know for some that is not a lot, but its what I got:p 

The problem now is that after a day I can't seem to find the share partition which is formatted in FAT32.  I can see, but it is inaccessable from the Admin--Disk section.

Some help on that would be great,

I even tried XP partition to see if the problem was there.

KK

---

### Post by catlett on 2006-05-20
You have to mount the partition to see it. If you didn't specify at install it won't be mounted. You need to do 2 things to get it mounted. Find out what partition it is on. Then make a directory to put it in.
The first is to find it ```
sudo fdisk -l
```
For example this is mine 
```
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7797    62629371    7  HPFS/NTFS
/dev/hda2            7798       10270    19864372+   f  W95 Ext'd (LBA)
/dev/hda3   *       10271       12161    15189457+  83  Linux
/dev/hda5            7798        8665     6972178+   b  W95 FAT32
/dev/hda6            8666        8795     1044193+   b  W95 FAT32
/dev/hda7            8796       10124    10675161   83  Linux
/dev/hda8           10125       10185      489951   82  Linux swap / Solaris
/dev/hda9           10186       10270      682731   82  Linux swap / Solaris
tj@ubuntu:~$

```
The * is ubuntu. The one you are looking for is Fat32. For further example I'm going to mount my Fat32 at /dev/hda5 and I'll call it sharedspace. You can call it whatever you want and you can mount it whereever but if you mount it in the /media folder it will put an icon on the desktop.
Lets make the directory ```
sudo mkdir /media/sharedspace
``` Now we'll mount it manually. This will mount it for this session. At the end I'll give you a link to Aysiu explaining how to make it permanent. ```
sudo mount /dev/hda5 vfat -t /media/sharedspace
```
That is it manually. If this works you now know where the partition is and you can follow Aysiu's instructions to make it permanent [http://www.ubuntuforums.org/showthread.php?t=174562](http://www.ubuntuforums.org/showthread.php?t=174562)
Good luck. See you around the forums.

---

### Post by KarmaKing on 2006-05-20
thanks for the reply I will try it soon as I figure out why my terminal screen ios not letting me type in password

KK

---

### Post by KarmaKing on 2006-05-20
OK, I followed psychicats ([http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)) instructions and this is what I got:

> Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


I also gave it which folder, but the folder has a lock over the icon and shows none of the files that are present that I placed there from within Windows.

---

### Post by KarmaKing on 2006-05-20
I also just rebooted and got a mounting error before the sign in screen

---

### Post by argie on 2006-05-20
From the fresh install of Ubuntu, I modified no files/folders except for one thing.

I created three folders in my home directory. (for c, d, e)
Then, I typed in:
**sudo mount /dev/hda1 ~/c**
from whereever, and, after entering that sudo password, I got to access the /home/george/c directory which had all the files/folders from C:\ on my windows system. (you'll have to change that '1' in /dev/hda1 probably)
When I edited fstab on RedHat 8 (long time ago) it used to keep trying to mount it at startup which used to take years, so I've let that go, and used this rather satisfactory option.

Another advantage is, this way that directory (/home/george/c) is usually given only root permission, so I don't accidentally mess it up while on Linux. I use the "Nautilus sudo" script and the usual sudo terminal thing to do anything to the stuff there. Most of the time it's just reading/copying and so I don't need to.
However, I have had no problem while writing files to that partition (with sudo cp). However, they were only upto 10MB in size.
Interesting that mount seems to auto-detect the format, from all those guides I wouldn't have known it could. By the way, any danger in this?

---

### Post by KarmaKing on 2006-05-20
Muuuuhaaha haa  Muuuuuha ha haaa haaa!!!!  Victory!!

I finally got it to work:D :D :D :D 

I just unmounted everything and then went by the steps real systematically and BAMM.  I got access.

Thanks to all for the help.

metta

KK

---

### Post by catlett on 2006-05-20
Just got back into the forums. These server changes are killing me. Glad it went well. Aysiu's instructions are always dead on. That was going to be my advice. Something must have been entered wrong. With Aysiu's stuff, it's right on and thorough. Always cut and paste. Then go in and change a number or letter.
Browse that psychocats site. It is mantained by Aysiu. If your stuck chances are Aysiu has already figured a way out for you.

---

