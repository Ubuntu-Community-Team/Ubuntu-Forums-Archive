---
title: "fsck system  exit status 8"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by petegreenhorn on 2007-05-01
**** hi need some help with this please, i searched these post and found the same problem that had been resolved , unfortunatly for me there were one or two differences .So i could not resolve the problem by following the said post . 
1. [COLOR="Red"] /var/log/fsck/checkfs [/COLOR] gave permission denied , so thats where i got to with my problem .

---

### Post by dstew on 2007-05-01
Are you trying to read that file? What program are you using to try to read it? You might need superuser privleges, since the directories are owned by root. To get temporary superuser privleges to do administrative tasks, use **sudo**. See: [http://www.gratisoft.us/sudo/](http://www.gratisoft.us/sudo/)

---

### Post by petegreenhorn on 2007-05-01
thanks for reply dstew  this is the thing after reading a similar resolved post i tried to follow what was done but fell at first hurdle in that i could not see the output of the command so am unable to get any further . P>S i am a  total noobie and would appreciate you're help if you have time
fogot to say that i'm trying to resolve a boot problem (fsck system error)

---

### Post by dstew on 2007-05-02
I am willing to help you. What exactly are you trying to do? What is the boot problem? What kind of Ubuntu are you trying to boot? Are you having trouble with a Live CD, or with an installed Ubuntu system? Also, post the link to the previous post that you are trying to follow.

---

### Post by petegreenhorn on 2007-05-02
Hi dstew thanks for your offer of help , my problem is as follows .when i boot into ubuntu edgy i get 
an error (fsck system exit status 8 ) having followed quite alot of links/ posts , i am still where i was 
pete@pete-desktop:~$ cat /var/log/fsck/checkfs
Log of fsck -C -R -A -a 
Wed May  2 12:31:11 2007

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=125ecefb-07e5-4c0a-af61-35484f248029'
Failed to open the device 'UUID=125ecefb-07e5-4c0a-af61-35484f248029': No such file or directory


fsck died with exit status 8

Wed May  2 12:31:11 2007
pete@pete-desktop:~$ Log of fsck -C -R -A -a 
bash: Log: command not found
pete@pete-desktop:~$ Wed May  2 12:31:11 2007
bash: Wed: command not found
pete@pete-desktop:~$ 
pete@pete-desktop:~$ fsck 1.39 (29-May-2006)
bash: syntax error near unexpected token `('
pete@pete-desktop:~$ fsck.ext3: Unable to resolve 'UUID=125ecefb-07e5-4c0a-af61-35484f248029'
bash: fsck.ext3:: command not found
pete@pete-desktop:~$ Failed to open the device 'UUID=125ecefb-07e5-4c0a-af61-35484f248029': No such file or directory
bash: Failed: command not found
pete@pete-desktop:~$ 
pete@pete-desktop:~$ 
pete@pete-desktop:~$ fsck died with exit status 8
fsck 1.39 (29-May-2006)
Usage: fsck.ext3 [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
                [-I inode_buffer_blocks] [-P process_inode_size]
                [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
                [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
pete@pete-desktop:~$ 
pete@pete-desktop:~$ Wed May  2 12:31:11 2007
bash: Wed: command not found
pete@pete-desktop:~$ 
sudo gedit /etc/fstab

---

### Post by petegreenhorn on 2007-05-02
having tried to repair the uuid settings for hda1 in fstab it did not alter anything.
system setup 
two hard drives maxtor  as follows           /dev/hda1  ext3      40.18 gb
                                                                         /dev/hda3   ext3      /, /dev,static/dev
                                                                                          2    extended       34.00gb
                                                                                          6    linux swap     1.07
                                                                                          5    linux swap      1.07
                              HD    as follows               hdb1         ntfs      /media/hdb1   47gb
                                                                         unallocated                                    29.58 
maxtor:
ubuntu edgy (the one i'm on at the moment )
xandros
HD:
windows

---

### Post by dstew on 2007-05-02
Let me explain a few things for you. This:
> pete@pete-desktop:~$ cat /var/log/fsck/checkfs
Log of fsck -C -R -A -a
Wed May 2 12:31:11 2007

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=125ecefb-07e5-4c0a-af61-35484f248029'
Failed to open the device 'UUID=125ecefb-07e5-4c0a-af61-35484f248029': No such file or directory

fsck died with exit status 8is the output of the fsck command that was run at boot time. The problem is the disk that it was supposed to check was not found. The rest of the output you list is the response to your command```
pete@pete-desktop:~$ Log of fsck -C -R -A -a
```You did not need to enter this command, and the output is meaningless.

We need to see the exact names of the file systems that are currently in your computer. To do this, enter this command on the command line, and post the output to the forum.```
sudo fdisk -l
```

---

### Post by petegreenhorn on 2007-05-02
pete@pete-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        5245    42130431   83  Linux
/dev/hda2            9685        9964     2249100    5  Extended
/dev/hda3            5246        9684    35656267+  83  Linux
/dev/hda5            9825        9964     1124518+  82  Linux swap / Solaris
/dev/hda6            9685        9824     1124487   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        6149    49391811    7  HPFS/NTFS
pete@pete-desktop:~$ 

sorry but i'm still finding my way in computing

---

### Post by dstew on 2007-05-04
Which partition are you trying to boot, is it /dev/hda1 or /dev/hda3?

---

### Post by petegreenhorn on 2007-05-05
it's hda1, and thats where the prob is the uuid's don't match but when i change it it makes no difference

---

### Post by dstew on 2007-05-08
We have to look at the /etc/fstab file in the Linux system on hda1. To do that, you need to boot from the Live CD and mount the /dev/hda1 onto the Live CD file system. Then you can look at, and edit, the /etc/fstab file.

Boot the Live CD. Open a terminal window and enter these commands:```
mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu
cat /media/ubuntu/etc/fstab
```
Post the result to the forum.

---

### Post by petegreenhorn on 2007-05-10
OK sorry for delay in response but work load as been heavy . 

ubuntu@ubuntu:~$ mkdir /media/ubuntu
mkdir: cannot create directory '//media/ubuntu' Permission denied
ubuntu@ubuntu:sudo mount -t ext3 /dev/hda1 does not exist
ubuntu@ubuntu:~$ cat  /media/ubuntu/etc/fstab
cat: /media/ubuntu/etc/fstab: No such file or directory
ubuntu@ubuntu:~$

---

### Post by dstew on 2007-05-11
Sorry, try```
sudo mkdir /media/ubuntu
```If it asks for a password, just hit enter.

---

### Post by kjaggu on 2007-05-12
I am sorry to butt in to this thread....

I am having the same problem as mentioned here. 

All the help would be of great use to me.. I,too. am following the same instructions. Will post my results once i get the Live Cd. Its not with me as of now. 

Regards,
Jaggu

---

### Post by andrewmp on 2007-11-18
Hi,
I get this error whenever I install a 2nd copy of Ubuntu on my machine on some other partition.  For some reason when you install the 2nd copy, it messes up your first's fstab by replacing all device names by some UIDs, so you must change them back.

> sudo gedit /etc/fstab

You will see something like this:
> 
...
#/dev/hda2
UID=87340-fjejfiodkfj800   ext3    defaults,errors=remount-ro 0       1
#/dev/hda1
UID=3f8f-3fd87j3kkk-8877
/media/hda1     ntfs    defaults,umask=007,gid=46 0       1
#/dev/hda4
UID=39f90-f98ff9993-ffed       /media/hda4     ntfs    defaults,umask=007,gid=46 0       1


You'll want to uncomment the device names and delete the UIDs like so:
> /dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
/dev/hda4       /media/hda4     ntfs    defaults,umask=007,gid=46 0       1

Save, quit and reboot and it should all be better!

---

### Post by Chymera on 2007-11-25
10x, i followed your instructions and i've got rid of the error i get at startup, however i still can't mount my drives :(

---

