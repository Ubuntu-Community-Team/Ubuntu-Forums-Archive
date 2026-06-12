---
title: "Empty partition after install"
date: 2013-05-02
forum: Any Other OS
---

### Post by tbk515 on 2013-05-02
Hi, All !
Until yesterday, I used/testing OpenSuse 12.3 and used my partition, mounted in "/mnt/point". When I reinstalls I dont format this partition also "/home". Today I decided to try again Ubuntu 12.04. And again shell annoyed me, then make Mint 13 install. When install  start I got a message "Can't mount point at /mnt/point!" or something that sort of thing. After install finished and start new system, My folder named "Point" doesn't exist :confused:
In OpenSuse for last using the folder contained over 110 GB from 120 GB. In Mint 13 I have 117 GB free space and some strange folders with names "at-spi2", "pulse-2L9K88eMlGn7", "pulse-PKdhtXMmr18n".
In that partiton I had some Music and Movie and don't carry them, I can download them again, but why My Folder is gone? Why the partition is broken. I used for last 6-8 months. My hard Toshiba is over 4 years old. The partition have not bad sector.
Pls, give me hope. Give me explanation for this case.
Tnx in advance and sorry for my bad English.

---

### Post by Perfect Storm on 2013-05-02
Moved to Other OS/Distro Support.

---

### Post by kiyop on 2013-05-03
Do not write anything onto the partition which contains your important files.
First, confirm that the partitiion you think to be the partition which contains your important files is really the partition which contains your important files.
```
sudo blkid
sudo parted -l
```
or palimpsest (gnome disk utility) or gparted may help you to confirm.

If it is really the partition which contains your important files, then confirm that you have enough access permission to the directories and the files in the partition.
```
sudo ls -l <mount point of the partition>
```
Replace the above words between "<" and ">" to proper word.
Do not type "<" and ">".
Read manuals to understand the output of "ls" by
```
man ls
```
You can check the mount point of the partition by
```
sudo mount
```
If the partition is not mounted, you can mount it onto /mnt (mount point of the partition) by
```
sudo mount -t auto <device file name of the partition> /mnt -o rw
```
I assume you use mint. I have a poor memory, but I remember that some linux distributions like sabayon mount some partitions onto a directory (such as windows) in /mnt. If you use such distribution, mounting onto /mnt may mess up your system.  

Device file name is like /dev/sda5.

If you do not have enough access permission, then you can change the owner of them by
```
sudo chown <your user name (account)>  -R <mount point of the partition>
```
You can also change the permission of them by
```
sudo chmod <permission combination> -R <mount point of the partition>
```
You can read manuals by
```
man chown
man chmod
```
or so.

If the partition which contains/contained your important files does not contain any of your important files, you might have formatted it.
Even so, you may be able to recover files by "photorec" or "testdisk"
You can install photorec, which is involved in "testdisk" package, and testdisk by
```
sudo apt-get update
sudo apt-get install testdisk
```

---

### Post by tbk515 on 2013-05-03
[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1246530")***kiyop***, Tnx for trying to help me, but today I started Mint 13 and Xubuntu 12.04 as LIVE user from Install CD and the result is: The buggy Mint is formatted the partition without my permissions. So I never use Mint again, until version 112 released. :mad:
Btw, I tried yesterday half of your suggestions without any success.
Tnx!

---

### Post by kiyop on 2013-05-03
> **tbk515 said:**
> The buggy Mint is formatted the partition without my permissions. 
...
Btw, I tried yesterday half of your suggestions without any success.
I am sorry to hear that.

> **tbk515 said:**
> Hi, All !
Until yesterday, I used/testing OpenSuse 12.3 and used my partition, mounted in "/mnt/point". When I reinstalls I dont format this partition also "/home". Today I decided to try again Ubuntu 12.04. And again shell annoyed me, then make Mint 13 install. When install  start I got a message "Can't mount point at /mnt/point!" or something that sort of thing. After install finished and start new system, My folder named "Point" doesn't exist :confused:
Read installation manual for mint before installing mint so that you will not lose your important data in future.

> **tbk515 said:**
> Why the partition is broken.
What did you do? Especially I cannot understand what you did about:
> **tbk515 said:**
> When I reinstalls I dont format this partition also "/home". Today I decided to try again Ubuntu 12.04. And again shell annoyed me, then make Mint 13 install.

Did you try testdisk and/or photorec? They sometimes recover well.

---

### Post by tbk515 on 2013-05-03
We, in Bulgaria don't read Users Manuals.:lolflag:

Yesterday tried to mount the partition, I changed permissions, but forgot to try rescue tools, because the media isn't so important.
Today I decided to migrate to XFCE for permanently. I loved Gnome 2.x.):P

---

