---
title: "ubuntu 6 server disk partition"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by gregkou on 2006-09-11
I am a newbie to linux, especially to ubuntu.
I was trying to install the 6 server version, but run into problem while partition the disk.
my hard drive is a 20.5 GB disk, and it will be all use for ubuntu 6 server.

the following partition is my plan
1.5 GB /
5 GB /usr
5GB /var
5GB /home
1GB /temp
512 MB SWAP
3.5 GB /backup

however, after I setup the 4th partition, the remaingin 3.5 GB space become unusable. and can't contaiue with the partition:( . I look all over the web try to find the answer but fail. is there something I did wrong? and if there is any place I can find related document for partition the drive for ubuntu? ](*,) ](*,) ](*,) 

Thanks alot for your help..
Greg

---

### Post by bodhi.zazen on 2006-09-11
If you are trying to install a desktop just use the default partitioning.

/swap = RAM x2
Rest in root /

The problem you have is you can only have 4 primary partitions on a hard drive. The solution is to use a logical partitioning.

You can make one of your primary partitions into an extended partition. An extended partition can then hav 4+ additional logcial partitions depending on BIOS.

Clear as mud?

---

