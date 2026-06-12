---
title: "Partition Issues &amp; Resize question"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by GreenMedallion on 2007-01-27
A couple weeks ago I noticed one of my original Dell Media partitions had duplicated itself on my drive. After some investigation of the fstab I found this second Dell Media drive was some sort of 'ghost' duplicate that popped up and mounted, but didnt really exist.

After further investigation - running Gparted, running my install CD to get to the partition edit table - I discovered NO partitions I originally installed are being recognized by the system. On top of this Windows does not boot at all. Ubuntu works just fine, however. 

So I really would like to repartition and NOT lose my precious ubuntu. It runs well, is customized how I like it, is configured appropriately, etc. Is it possible to repartition & resize ubuntu, and then add a new Swap and /home ? 

My current fstab is below. As you can see, a mess! Due to pre-installed Dell partitions, plus windows, plus a shared fat32, etc, etc. 

final question - will I be able to put windows on the /home at a later time?


Current fstab -

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=0222,gid=46 0       0
/dev/sda4       /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda7       /windows        vfat    defaults,iocharset=utf8,umask=000,gid=46 0       0
/dev/sda8       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Patrick-Ruff on 2007-01-27
you don't need those bullshit dell-pre-installed partitions. 

first, backup your ubuntu stuff.

second, boot up a live cd and open gparted.  

erease those dell partitions and then extend the size of your ubuntu partition.

if it screws up, well, be happy you backed up ;).

also, I don't think windows is capable of using the same partition as linux, it just wouldn't work well.  unless you want to run it in VMWARE


and if you still can't find these partitions, back up your entire ubuntu partition and then nuke your entire hard drive . . .  

check this out : [http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by climbjm on 2007-01-27
For what it's worth...

Buy the Acronis Disk Director Suite.  I did and It was some of the best money I've ever spent.  I have enjoyed it more than Norton and Partition Magic. :D

---

### Post by GreenMedallion on 2007-01-27
I agree Patrick. In fact I am suspicious it was the Dell Restore that did this in the first place, since it has permissions to do whatever.

So my question. How can I back up my "entire ubuntu partition" and then restore a new install to those settings? Is it has simple as using the Simple Backup programs under System/Administration?

---

