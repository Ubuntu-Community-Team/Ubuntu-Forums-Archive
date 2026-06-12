---
title: "fsck size problem on bootup"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by geoffkaniuk on 2007-06-15
Hi,

I am getting  boot-up errors on Feisty Fawn and I really would appreciate help on this one.

The first error a few days ago was "The superblock could not be read".  I posted details of this on April 13 2007  in a reply to a post by wadeall  "fsk problem" .

The problem has now changed to "Error determining size of the physical device", and here is the log:

> Log of fsck -C -R -A -a 
Fri Jun 15 10:02:03 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/.tmp-254-1: Error determining size of the physical device: No such file or directory
fsck died with exit status 8

Fri Jun 15 10:02:03 2007


The message then goes on to say "Fix the file system  manually" - but how do I do that?

Again CTRL+D does continue the boot and then all seems to function normally.

This is a worry, so I would appreciate some guidance as to whether this is a very serious problem and how do I go about fixing it.

Many thanks for your help,

Geoff  :sad:

---

### Post by Herman on 2007-06-15
Hello geoffkaniuk,
First you should of course make sure you have a backup of all your important data, you should do that all the time anyway. 

File system checks should not be done with the file system mounted, so it's normally best to use a LiveCD system to run the file system check from. Any Live CD will do. The Ubuntu Live CD is good for that.

You can run a file system check manually in a terminal in your Live CD..
The first thing you'll need to find out is which partition to tell the file system checking program to work on, you would be able to do that by looking at your hard disk with any disk partitioner. You can use fdisk for that by typing 'sudo fdisk -lu' into your terminal.
> sudo fdisk -luLet's say for example you see that your Ubuntu partition is called /dev/hda2.
Then providing your Ubuntu has the standard ext3 file system you would run, ```
sudo e2fsck -C0 -f -p -v /dev/hda2
```Wait while that does its work and prints out a report.
Likely it will tell you what to do next if it can't fix everything itself. You could copy that result and post it here if you can, it could be interesting.  :D
Probably then you'll need to run something a little stronger like 'sudo e2fsck -f -y -v /dev/hda2', ```
sudo e2fsck -f -y -v /dev/hda2
```....and wait until that finishes and see what you have to do next or it may fix everything.  
Try those two commands for a start and see what happens, probably that's all you'll need to do, Please reply with the results if you can. :)
Regards, Herman

---

### Post by geoffkaniuk on 2007-06-18
Hi Herman,

Many thanks for your response and detailed instructions.

I ran the file check as you suggested and here are the complete logs:

> SIZE PROBLEM
Log of fsck -C -R -A -a 
Fri Jun 15 10:02:03 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/.tmp-254-1: Error determining size of the physical device: No such file or directory
fsck died with exit status 8

Fri Jun 15 10:02:03 2007
----------------

PARTITION LIST
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   109450844    54725391   83  Linux
/dev/sda2       150352335   156296384     2972025    5  Extended
/dev/sda3       109450845   150352334    20450745   83  Linux
/dev/sda5       153324423   156296384     1485981   82  Linux swap / Solaris
/dev/sda6       150352461   153324359     1485949+  82  Linux swap / Solaris

Partition table entries are not in disk order

BASIC CHECK
ubuntu@ubuntu:~$ sudo e2fsck -C0 -f -p  -v /dev/sda1
                                                                               
  187603 inodes used (2.74%)
    3468 non-contiguous inodes (1.8%)
         # of inodes with ind/dind/tind blocks: 9831/114/0
 1403393 blocks used (10.26%)
       0 bad blocks
       0 large files

  150734 regular files
   19694 directories
     364 character device files
      59 block device files
       3 fifos
     507 links
   16735 symbolic links (14610 fast symbolic links)
       5 sockets
--------
  188101 files

STRONGER CHECK
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.40-WIP (14-Nov-2006)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  187603 inodes used (2.74%)
    3468 non-contiguous inodes (1.8%)
         # of inodes with ind/dind/tind blocks: 9831/114/0
 1403393 blocks used (10.26%)
       0 bad blocks
       0 large files

  150734 regular files
   19694 directories
     364 character device files
      59 block device files
       3 fifos
     507 links
   16735 symbolic links (14610 fast symbolic links)
       5 sockets
--------
  188101 files

I also ran the checks on sda3 and they produced the same results i.e. 0 bad blocks, 0 large files and no instructions to fix anything.  I have the output  if this is useful to you.  Whenever I get  these problems, after continuing the boot with CTR+D, the system remains fine and survives even through a complete switch off and power on.

On Saturday's boot up, I got the Superblock problem.  I then left the live CD in the tray ready for Sundays boot up and file check.  Here are the logs:

> SUPERBLOCK PROBLEM
Log of fsck -C -R -A -a 
Sat Jun 16 10:52:04 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/.tmp-254-1

/dev/.tmp-254-1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Sat Jun 16 10:52:05 2007
----------------

PARTITION LIST
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   109450844    54725391   83  Linux
/dev/sda2       150352335   156296384     2972025    5  Extended
/dev/sda3       109450845   150352334    20450745   83  Linux
/dev/sda5       153324423   156296384     1485981   82  Linux swap / Solaris
/dev/sda6       150352461   153324359     1485949+  82  Linux swap / Solaris

Partition table entries are not in disk order

BASIC CHECK
ubuntu@ubuntu:~$ sudo e2fsck -C0 -f -p -v /dev/sda1
                                                                               
  187629 inodes used (2.74%)
    3458 non-contiguous inodes (1.8%)
         # of inodes with ind/dind/tind blocks: 9839/116/0
 1406410 blocks used (10.28%)
       0 bad blocks
       0 large files

  150758 regular files
   19695 directories
     364 character device files
      59 block device files
       3 fifos
     507 links
   16735 symbolic links (14610 fast symbolic links)
       6 sockets
--------
  188127 files

STRONG CHECK
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.40-WIP (14-Nov-2006)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  187629 inodes used (2.74%)
    3458 non-contiguous inodes (1.8%)
         # of inodes with ind/dind/tind blocks: 9839/116/0
 1406410 blocks used (10.28%)
       0 bad blocks
       0 large files

  150758 regular files
   19695 directories
     364 character device files
      59 block device files
       3 fifos
     507 links
   16735 symbolic links (14610 fast symbolic links)
       6 sockets
--------
  188127 files


Again I don't seem to be capturing the problem.

Today's boot up was normal i.e. from the hard disk, and today there was no problem.  I have however seen this before, and the problem just recurs the next day.

When the problem does occur, one is invited to press CTRL+D to continue the boot, or enter the  root password to repair manually.  Is it safe to try the latter option next time?

---

### Post by Herman on 2007-06-18
Hello geoffkaniuk
Those file system checks look okay to me. :D

I wonder if your /etc/fstab file has the right file system UUID numbers in it for the file systems you have right now. 
Often these are changed by partition editing software, can you remember working on your partitions and file systems before this problem first stated?
In any case, a good way to check is to run the command 'blkid' from a hard disk installed system or 'ls /dev/disk/by-uuid/ -alh' from a Live CD or hard disk installed system. Either of those commands will give you a list of your file system's UUID numbers.```
blkid
```or,```
ls /dev/disk/by-uuid/ -alh
```In another terminal get your /etc/fstab file with 'sudo gedit /etc/fstab' 
```
sudo gedit /etc/fstab
```Then compare the list of partitions and UUID numbers with what's in your /etc/fstab file. If they don't agree with each other copy the UUID numbers from the blkid comand or ls /dev/disk/by-uuid/ -alh command and paste them in the appropriate places in your /etc/fstab file to update it with the currently correct information. Save and close the file. That should fix the problem.
If you need help, post a copy of your /etc/fstab file here and the output from those commands and I or someone else will do it for you and post back the corrected /etc/fstab. (If that's the problem - likely that's all it is).  It's not very hard to fix. :D
Regards, Herman :D

EDIT, What's this " /dev/.tmp-254-1" in your /etc/fstab file for anyway?  Any idea what that is? I haven't seen that before, maybe that's your problem. Can you post your /etc/fstab file here please? You could try 'commenting' that out and if your system works okay just leave it out unless it's for something.

---

### Post by geoffkaniuk on 2007-06-19
Hello Herman,

I have not worked on my partitions or filesystem.  The problems started after the online upgrade from Edgy to Feisty.

Today it was a superblock problem.  The UUID's look identical - here is the output:

> LATEST fsck LOG
Log of fsck -C -R -A -a 
Tue Jun 19 08:11:06 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/.tmp-254-1

/dev/.tmp-254-1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Tue Jun 19 08:11:06 2007
----------------

BLOCK IDENTIFIERS
geoff@geoff-desktop:~$ blkid
/dev/evms/sda6: TYPE="swap" 
/dev/sda1: UUID="b37f7a67-acc5-4c84-82a4-8b475d7dfc24" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="c048d8f4-e591-4634-a962-73cd610b3dd0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="2591c4ed-fe74-4def-a1e0-3ac369703f29" TYPE="swap" 
/dev/sda6: TYPE="swap" 
/dev/evms/sda1: UUID="b37f7a67-acc5-4c84-82a4-8b475d7dfc24" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/sda5: UUID="2591c4ed-fe74-4def-a1e0-3ac369703f29" TYPE="swap" 
geoff@geoff-desktop:~$ 

FSTAB
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=b37f7a67-acc5-4c84-82a4-8b475d7dfc24 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=c048d8f4-e591-4634-a962-73cd610b3dd0 /media/sda3 ext3 defaults 0 2
# /dev/sda5 -- converted during upgrade to edgy
UUID=2591c4ed-fe74-4def-a1e0-3ac369703f29 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0




There is no /dev/.tmp-254-1 in my fstab file,  it just appears as part of the error log.

During boot up I watch the progress bar.  This gets about halfway pretty quickly, then there is sudden heavy and audible disk activity.  Then the screen fills with the error messages.
This time I tried typing my root password which was the other option I was given in order to fix the file system manually.   All I got was:

bash: no job control in this shell
bash: groups: command not found.
bash: lesspipe: command not found
The program apt-get is currently not installed.  You can install it by typing apt-get.
Warning: no final newline at the end of  /etc/fstab

The very last line of fstab is indeed terminated by 0 , no newline.   I have now corrected fstab to include the terminating newline.  I will see what happens tomorrow.

Thanks very much for your continuing interest in this problem!

---

