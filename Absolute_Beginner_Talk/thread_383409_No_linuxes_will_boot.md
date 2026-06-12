---
title: "No linuxes will boot"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Twiggy003 on 2007-03-13
I have Ubuntu 6.10, Xubuntu 6.10, PClinuxOS, and Zenwalk installed. I wanted to reinstall Zenwalk, and i had some troubles doing so, it gave errors that the destination was full when it wasnt.  so i rebooted back into my other linuxes and they wouldnt boot giving harddrive errors saying that partitions didnt exist. then i used System Rescue Cd and loaded up gParted and all the partitions on my secondary harddrive (linux harddrive) had exclamation marks by them, and i tried to run a check and repair on the gparted and it gave an error message:

GParted 0.3.3

Libparted 1.7.1

Check and repair filesystem (ext3) on /dev/hdb2  00:00    ( ERROR )
     	
calibrate /dev/hdb2  00:00    ( SUCCES )
     	
path: /dev/hdb2
start: 63
end: 112647779
size: 112647717 (53.71 GiB)
check filesystem on /dev/hdb2 for errors and (if possible) fix them  00:00    ( ERROR )
     	
e2fsck -f -y -v /dev/hdb2
     	

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

e2fsck 1.39 (29-May-2006)
e2fsck: No such file or directory while trying to open /dev/hdb2 


- im slightly noobish when it comes to linux but ive used it for a year or so.

any help would be great.

---

### Post by haelters on 2007-03-13
It might be that the partition table got screwed. Does gparted still show you the partitions as you expects them ? Can you send the output of 
<code>parted /dev/hdb print</code>

If the partitions got screwed up, you might try gpart, but it is quite dangerous...

---

### Post by Twiggy003 on 2007-03-13
Thanks for the reply.  Yes it shows them as i created them, just all the partitions have exclaimation marks beside them.

the output of parted goes:

Disk geometry for /dev/hdb: 0.000-114473.460 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
2          0.031  55003.798  primary   ext3
4      55003.799 109003.535  extended
7      55003.860  79007.167  logical   ext3
6      79007.199  94005.351  logical   ext3
5      94005.352 109003.535  logical   ext3
3     109003.535 109999.753  primary   linux-swap
1     109999.753 114470.969  primary   fat32       boot
Information: Don't forget to update /etc/fstab, if necessary.


thanks for t'help.

---

### Post by haelters on 2007-03-13
Try to run e2fsck -f -y -v -b 8193 /dev/hdb2. 

Also, could you send the output of ls -l /dev/hdb*. It might also be that the major/minor numbers of the block device are wrong.

---

### Post by Twiggy003 on 2007-03-13
ok, well from sudo e2fsck -f -y -v -b 8193 /dev/hdb2 i got:

e2fsck 1.38 (30-Jun-2005)
e2fsck: No such file or directory while trying to open /dev/hdb2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

and also from sudo ls -l /dev/hdb i got:

brw-rw----  1 root disk 3, 64 2007-03-13 16:52 /dev/hdb

with sudo ls -l /dev/hdb2 i got:

ls: /dev/hdb2: No such file or directory

im doing all this from the Ubuntu Breezy Badger live CD (as im lending Edgy out to someone else)

---

### Post by haelters on 2007-03-13
strange, your /dev/hdb? block devices are missing. Try to create them by hand with the following command:
sudo mknod /dev/hdb2 b 3 66
and try then to mount your disk 
sudo mkdir /mnt/hdb2
sudo mount /dev/hdb2 /mnt/hdb2

if this does not work try the e2fsck -f -y -v -b 8193 /dev/hdb2 again.

---

### Post by dannyboy79 on 2007-03-13
i would say that your partition table got messed up. can't you use fdisk somehow to rewrite the partition table? i remember seeing this other guy who had partition expert informing him that his partitions were invalid also just like gparted is giving you exclamation points over them. try to just do sudo fdisk /dev/hdb and see what happens. or do man fdisk, and it should explain that using the fdisk command will "recheck" the partition table in effect rewriting it. good luck

---

### Post by Twiggy003 on 2007-03-13
ok i tried that,

ubuntu@ubuntu:~$ sudo mount /dev/hdb2 /media/hdb2
mount: you must specify the filesystem type

usually i dont have to type in a file system type, so i tried

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdb2 /media/hdb2
mount: /dev/hdb2 is not a valid block device

and also:

sudo e2fsck -f -y -v -b 8193 /dev/hdb2
e2fsck 1.38 (30-Jun-2005)
e2fsck: No such device or address while trying to open /dev/hdb2
Possibly non-existent or swap device?

thanks for all so far.

---

### Post by dannyboy79 on 2007-03-13
simply typing in sudo fdisk -l should rewrite your partition table and your hdb2 should return. good luck

per the man page:
Whenever a partition table is printed out, a consistency check is  per-
       formed  on  the  partition table entries.  This check verifies that the
       physical and logical start and end points are identical, and  that  the
       partition  starts and ends on a cylinder boundary (except for the first
       partition).

---

### Post by Twiggy003 on 2007-03-13
ok, thanks, but:


Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/hda2           16709       30401   109989022+   7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?       14024       14593     4578525    b  W95 FAT32
/dev/hdb2               1        7012    56323858+  83  Linux
/dev/hdb3           13897       14023     1020127+  82  Linux swap / Solaris
/dev/hdb4            7013       13896    55295730    5  Extended
/dev/hdb5           11985       13896    15358140   83  Linux
/dev/hdb6           10073       11984    15358108+  83  Linux
/dev/hdb7            7013       10072    24579387   83  Linux

Partition table entries are not in disk order


shall i try putting hdb in there somewhere?

many thanks, would hate to have to reformat it all.

---

### Post by dannyboy79 on 2007-03-13
don't know what you mean, "shall i try putting hdb in there somewhere?"
i am not sure what to suggest, according to the man page, all fdisk does is read the disk and write out the partition table, so this is weird!!! not sure what to tell you? did you retry to boot any of your linux's?

found this: [http://phlogma.com/linux/?p=4](http://phlogma.com/linux/?p=4)
hope it helps ya.

---

### Post by dstew on 2007-03-13
fdisk is telling you that the /dev/hdb partition table has some flaws in it. I think the question mark where the boot marker should be might a sign of the same thing. You would need to fix the partition table. The partition in question seems to be FAT32. Have you tried the Windows fdisk program to take a look at it? Maybe it would be more able to fix it.

---

### Post by dannyboy79 on 2007-03-13
if my previous link didn't help, here's another that should point you in a good direction. you basically need to rewrite the partititon table based on the output of fdisk but obviously making sure they're in order  i would think

---

### Post by dstew on 2007-03-13
Check this thread, especially post #5

[http://ubuntuforums.org/showthread.php?p=2110885](http://ubuntuforums.org/showthread.php?p=2110885)

---

### Post by Twiggy003 on 2007-03-13
Ok, ive just run testdisk and gone through the prompts and wrote the changes n such. thanks for all your suggestions and help. going to find out if its worked. thanks

---

### Post by Twiggy003 on 2007-03-13
right, i rebooted back to the live cd and still i cannot mount my linux partitions. Im too tired to concentrate right now, but i shall look through the posts again and attempt to get it to work. thank you for all your help, any other suggestions of what to do would be great. many thanks of so far.

---

### Post by Twiggy003 on 2007-03-14
Crap, after trying testdisk and such, i wrote what looked like the correct table and now when i load gparted it looks very little like how i created it to begin with, im trying testdisk now and hoping that it'll somehow sort it all out.  any help would be...helpful.

---

### Post by dannyboy79 on 2007-03-14
fdisk already showed you what your disk looked like, you just need to make sure that the numbers were correct relation to the devices. did you read all the threads I linked to?

---

### Post by Twiggy003 on 2007-03-14
ive read through all of them, i dont quite understand all of them, i tried testdisk and i have next to no knowledge of fdisk,  and if the numbers dont match, how to i enter it all in?  just seems to keep annoying me more than anything.  sorry for being quite the noob at this, is there any simple step by step procedure i can do to get this sorted?

---

### Post by dannyboy79 on 2007-03-14
well this link gives you step by step instructions so I am not sure what you need to understand about fdisk, it tells how to fix it. now I can't gurantee that this will work but his problem sure looks exactly like yours. good luck. otherwise have to tried to use part image and just create an image of each of the partitions? it's in my sig.

---

### Post by Twiggy003 on 2007-03-14
ok thanks, i shall try that. i only really care about hdb2, which gpart seemed to of guessed rightly, but upon it guessing it right it hasnt wrote it to table, or isnt it meant to do that? i shall try a few more things then i'll try that Partimage. many thanks

---

### Post by dannyboy79 on 2007-03-14
also, here is a great guide for parted. [http://www.gnu.org/software/parted/manual/parted.pdf](http://www.gnu.org/software/parted/manual/parted.pdf)
according to this you can first delete all your partitions, then use the rescue command and you can use the numbers you were given when you first used parted, this might work? or maybe try to use mkpart, which will create a partition for your info but not format it! good luck

---

### Post by Twiggy003 on 2007-03-14
Brilliant! :) parted created a partition without killing everything just like you said. everything seems to be in order here, i shall work on reinstalling GRUB or and getting it booted again, and even if the worst comes to the worst, at least i can see my files to back them up. :)

---

### Post by dannyboy79 on 2007-03-14
AWESOME!!!!!!!!! so you're saying that you can at least mount your partition now? also, after you fix grub and fstab if need be and then you finally can boot into each one of your partitions please come back and let us all know this way I can mark this thread and possibly write up a how-to as this sounded like a serious issue but it is solvable as we have found out!!!

---

### Post by Twiggy003 on 2007-03-20
sorry for the late reply, much going on, and to save time, im just going to back it all up and start again im afraid, Slackware 11, PClinuxOS, Xubuntu and Ubuntu...maybe wait til feisty fawn for ubuntu and use the other linuxes, just incase there are any upgrading complications.  thanks for all, just getting the data off is brilliant.

---

