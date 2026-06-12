---
title: "Partition locations on disk?"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by duketg on 2007-11-17
Hello all, short time lurker first time poster here.  I'm setting up my Gutsy 64bit install on my desktop right now (dual booting w/ XP for training wheels/assured WoW access), and I came up with a question about partitions.

I was following psychocat's partition guide, and decided to go with 5 partitions total.

XP partition (ntfs) 20GB
Shared data area (ext3) 80GB 
Home partition (ext3) 40GB
Root partition (ext3) 18GB
Swap partition 1GB

And I set them up in that order on the drive, because I couldn't find anything about recommended locations.  Does it really matter where on the physical drive you put the partitions?  I chose this order because that was what was in the picture in the guide.

Corollary:  Does my partitioning scheme seem reasonable?  I have a second hard disk where I backed up all my important data, which isn't reflected above.  Would any of you gurus have done this differently?  This is my first linux install, so I'm really just playing by ear.  I figure if worst comes to worst I can always reinstall and repartition.  Oh, I also started this whole process by wiping my main drive and reinstalling XP first (it was about time -- this is what got me thinking about installing Ubuntu in the first place...I hear this is unnecessary, which sounds great to me).

Oh, one more thing:  I had to make the swap partition a logical partition.  The other four are primary partitions, in case that affects anything.

Thanks for the advice, I've really learned a lot just reading the posts on here already!

---

### Post by Inxsible on 2007-11-17
No it doesn't matter that much as to where the partitions are. But generally the swap is put at the end because the automatic installer also puts it at the end.
Logical partitions are fine for linux. In fact I have my entire linux install in logical partitions including the root and the home. Windows however will not install in Logical partitions. it needs primary partition for the OS to install.

I think a 40 GB home is excessive ...especially since you have a separate shared space (ext3). I have 20 Gb of home and only 1 GB is currently used. This after installing a bunch of apps. The home folder is actually used to store user settings and its hard for simple txt or config files to take too much space.

I am assuming of course that you will keep your music and movies and pics and such on the shared space (thats what I do) so i find the 20 GB to be excessive and wasted too :(

I would give some of that space to the shared drive.

This is my partitions on a 160 Gb drive:
Windows Vista  - 25 GB (thats the minimum it would let me shrink. Vista is a hog )
Windows Data/apps - 15 GB ( for windows programs like turbotax, picasa2 etc)
/   - 9 GB
/home - 20 GB (which i think is too much)
shared - 80 GB
swap - 1GB

That would give you an idea. you can of course choose to make partitions any way you want

---

### Post by Inxsible on 2007-11-17
Oh and before you install Ubuntu, make sure you defrag the XP first. I know you just installed it, but just to be on the safer side defrag is 2-3 times at least.

---

### Post by duketg on 2007-11-17
Doh, I already installed it using those sizes.  Didn't defrag XP either.  Everything seems to be doing OK though.  WoW still works, which is my main concern anyway :)  I guess I can always resize the partitions using gparted though, correct?  Or is that a bad idea, since I've already set up everything?

Here's one thing I don't understand: When I open up file browser, I have the following drives in my computer:

CD-RW
File System
Floppy 1
hda1
hda2
Local Disk

as far as I can tell....
Local disk is my second hard drive, 
Filesystem is /root
hda1 is my XP partition
hda2 is my shared partition
by process of elimination, I think this makes Floppy 1 my /home partition (I don't have a floppy drive), but i can't seem to access it.  Also, there is a home folder in File System, so I'm starting to think things didn't go as smoothly as I thought. 

Here's the output of fstab, if that helps at all:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=5797d492-12ec-4d73-9182-6459919e048f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=ea9f913d-c0b4-4d83-8369-28c11eb97bc9 /home           ext3    defaults        0       2
# /dev/hda1
UUID=8414113214112926 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=9996423c-6b64-4df7-9837-2f462700ed76 /media/hda2     ext3    defaults        0       2
# /dev/hdd1
UUID=E4E475DCE475B202 /media/hdd1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=3dd87542-bf26-439d-b058-316d567b1cb8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

and here's fdisk -l

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefe1efe1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2           17140       19457    18619335    5  Extended
/dev/hda3            2551       12276    78124095   83  Linux
/dev/hda4           12277       17139    39062047+  83  Linux
/dev/hda5           19336       19457      979965   82  Linux swap / Solaris
/dev/hda6           17140       19334    17631274+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d192d19

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        9728    78140128+   7  HPFS/NTFS
```

and here's df -h (I don't know what that command stands for, but I saw it in another post)

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6              17G  2.3G   14G  15% /
varrun                503M   88K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
udev                  503M   92K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M   38M  466M   8% /lib/modules/2.6.22-14-generic/volatile
/dev/hda4              37G  190M   35G   1% /home
/dev/hda1              20G  5.9G   14G  31% /media/hda1
/dev/hda3              74G  180M   70G   1% /media/hda2
/dev/hdd1              75G   56G   19G  75% /media/hdd1
```

if there's any more info that's usefull, I'll post it, though it may not show up 'till tomorrow...

thanks for the help!

---

### Post by Inxsible on 2007-11-17
you can always resize partitions using gparted. but you won't be able to merge them to other existing partitions unless you format them again.

Meaning, you will have to copy the data over to the other partition and then merge it and then re-copy the data back.

Of course, you cant do this with the /root partition, because otherwise you will have to re-install the OS which would not make any sense. 

else you could have done everything over :D

---

### Post by Inxsible on 2007-11-17
df stands for *d*isk *f*ree

Linux is different than windows. Even though you see /home under the root (/ ) it is still a different partition (provided you created a separate partition and mounted it at /home during install). You can even do this in Windows, i.e. create partitions out of individual folders, but its not as intuitive in Windows.

I don't know why it would recognize a floppy drive when you don't have one. But if you remove that entry from fstab and then do ```
mount -a
``` i think it will get rid of it.

Local disk would probably be your Windows drive, since most drives in Windows are name Local Disk. Linux tends to grab the disk label and mount it using that name. My Windows drive was labeled Windows Data, and it automatically mounted it at Windows Data. So just check the data in there and if you see a Windows folder in there, then it probably is your windows partition (C Drive)

---

### Post by meindian523 on 2007-11-17
Usually,to avoid BIOS problems,it's recommended to keep the / partition up front where the BIOS can access the System files(Windows) and kernel and init(Linux),though if everything's working fine,nothing to worry,,,,,,,,,,,,,

---

### Post by duketg on 2007-11-17
After rummaging through the other drives, I know that local disk is my second hard drive, hda1 is XP, and hda2 is the shared area.  

If I right click the floppy and go to properties, it shows it as having 13.5 GB of free space. Is there any way that some of my hd wasn't allocated to a partition during install, and is now showing up as a floppy?

I'm starting to wonder if I shouldn't just reinstall from the live CD.  I haven't done anything with ubuntu yet, so it's not like I have any settings I'd lose, and then I could drop down the home and root partition sizes.

---

