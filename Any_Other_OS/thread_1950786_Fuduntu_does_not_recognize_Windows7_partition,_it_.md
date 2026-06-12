---
title: "Fuduntu does not recognize Windows7 partition, it wants install on the whole disk"
date: 2012-04-01
forum: Any Other OS
---

### Post by awayguy on 2012-04-01
Halo

i searched a little for solutions but didnt find anything really helpful.
My problem:

i've installed Win7 pro 64 bit on 160GB of my 300GB harddisk. I created also a 2nd Partition (with the help ov Windows7 CD) of 140GB. I didnt install anything on that 2nd 140GB partition. Now i want install there Fuduntu.
(Fuduntu because its a toshiba n550d netbook, some said fuduntu works fine on netbooks)

So i'm booting form the fuduntu usb installer. Then i choose "install on harddsik". Then i can only choose to install fuduntu on the whole Harddisk. There is no option to choose this 140GB partition or any other option to install it on less than 300GB.

How to install it on these free 140GB?

---

### Post by oldfred on 2012-04-01
Moved to OtherOS sub forum.

Hopefully you have not created more than the 4 primary partitions allowed. Windows will convert from basic partition to dynamic which does not work with Linux.

Post this from liveCD.

```
sudo fdisk -lu
```You cannot create Linux partitions in Windows and Ubuntu will read/write NTFS partitions, but cannot install to them as they do not support Linux permissions and ownership.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Use gparted to create partitions, then manual install to choose & format those partitions.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

