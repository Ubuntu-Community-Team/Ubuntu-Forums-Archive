---
title: "I like most people here need help."
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by shawnanigans on 2006-12-10
I was trying to shrink the size of my primary partition on my 120gb sata hard drive using Partition Magic in windows. It said I had to restart and now my PC wont start so I am trying to use the Edgy Eft Live CD to recover the data if possible but I can't get the drive mounted. So I am here to ask help with 2 things, the first is needed and that is to access the drive somehow and the second is to perhaps repair the drive somehow.

---

### Post by user1397 on 2006-12-10
> **shawnanigans said:**
> I was trying to shrink the size of my primary partition on my 120gb sata hard drive using Partition Magic in windows. It said I had to restart and now my PC wont start so I am trying to use the Edgy Eft Live CD to recover the data if possible but I can't get the drive mounted. So I am here to ask help with 2 things, the first is needed and that is to access the drive somehow and the second is to perhaps repair the drive somehow.try this (it worked for me): [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by igknighted on 2006-12-10
As a rule, don't ever use partition magic with linux, they don't get along well.  Always use Gparted or some other linux solution.

---

### Post by aysiu on 2006-12-10
Can you post the output of this terminal command? ```
sudo fdisk -l
``` That's a lowercase L at the end, not an uppercase i or the number one.

---

### Post by shawnanigans on 2006-12-10
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 60.0 GB, 60011642368 bytes
255 heads, 63 sectors/track, 7295 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          14      112423+   0  Empty
/dev/sdc2              15        7296    58492665    b  W95 FAT32


ubuntu@ubuntu:~$ mount /dev/drive /mnt/point
mount: only root can do that
ubuntu@ubuntu:~$ sudo /dev/drive /mnt/point
sudo: /dev/drive: command not found
ubuntu@ubuntu:~$ root /dev/drive /mnt/point
bash: root: command not found
ubuntu@ubuntu:~$ sudo mkdir /media/windows
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda /media/windows 
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /media/windows 
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/hda1 /media/windows
mount: special device /dev/hda1 does not exist
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /media/windows
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sdb1 /media/windows
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda  /media/windows
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sdc /media/windows
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sdd /media/windows
mount: special device /dev/sdd does not exist
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sdc1 /media/windows
^[[Amount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sdc2 /media/windows
mount: /dev/sdc2 already mounted or /media/windows busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/windows
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sdc2 /media/sdc2
mount: mount point /media/sdc2 does not exist
ubuntu@ubuntu:~$ sudo mkdir /media/sda1
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /media/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The part after the fdisk is just the stuff I have tried to do without result.

---

### Post by aysiu on 2006-12-10
So it's the 120 GB you're trying to mount? Or all of them? Well, let's start with the 120 GB one: ```
sudo mkdir /media/recovery
sudo mount -t ntfs /dev/sda1 /media/recovery -o nls=utf8,umask=0222
``` Then go to /media/recovery and see if you can see your files.

**Edit**: Never mind. I guess you tried that already: ```
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /media/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so
``` Usually that error means you have the wrong filesystem, but since you specified NTFS, we know that's not the case. That's not good. That means you probably have a bad superblock, which means you probably need to use something like *dd_rescue* to save your drive:
[http://ubuntu.wordpress.com/2006/01/21/rescue-data-from-failing-partition/](http://ubuntu.wordpress.com/2006/01/21/rescue-data-from-failing-partition/)

---

### Post by shawnanigans on 2006-12-10
I don't have enougg free space to copy my drive with ddrescue is there any way to repair the partition so I can just access it, a software version of the hard drive in the fridge perhaps, because I only need to get some few important files.

---

### Post by quarkhirad on 2006-12-11
> **shawnanigans said:**
> I was trying to shrink the size of my primary partition on my 120gb sata hard drive using Partition Magic in windows. It said I had to restart and now my PC wont start so I am trying to use the Edgy Eft Live CD to recover the data if possible but I can't get the drive mounted. So I am here to ask help with 2 things, the first is needed and that is to access the drive somehow and the second is to perhaps repair the drive somehow.

ok try this. 

:~$ sudo su
Password:
# mkdir /mnt/temp
# mount /dev/sda1 /mnt/temp/


offcourse this is to mount only the sda1 partition to mount more partions just keep repeating the mkdir comands and mount comands

like 
:~$ sudo su
Password:
# mkdir /mnt/temp1
# mount /dev/sdb1 /mnt/temp1/

---

### Post by shawnanigans on 2006-12-11
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mkdir /mnt/temp
root@ubuntu:/home/ubuntu# mount /dev/sda1 /mnt/temp
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:/home/ubuntu# mount -t ntfs /dev/sda1 /mnt/temp
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:/home/ubuntu# 

This is what i got from trying what quarkhirad suggested. Is there some way to repair the superblock?

---

### Post by quarkhirad on 2006-12-17
> **shawnanigans said:**
> ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mkdir /mnt/temp
root@ubuntu:/home/ubuntu# mount /dev/sda1 /mnt/temp
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:/home/ubuntu# mount -t ntfs /dev/sda1 /mnt/temp
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:/home/ubuntu# 

This is what i got from trying what quarkhirad suggested. Is there some way to repair the superblock?


dear shawnanigans

i suppose there is a better way to repair a superblock ](*,) . But i just reformat the partition. I know u will loose all ur data on that patition :( :(  . 

Bye  the way if u are dual booting with windows try booting into windows and then back up that partitions data and the format it.  :-k :-k :-k  

U can try this if ur not succesfull with option two then i would suggest wait for sometime  for someone to give u an idea on how to repair ur superblock. Before u format ur partition and loose all ur data.;) ;) 


all the best 


cheers

---

