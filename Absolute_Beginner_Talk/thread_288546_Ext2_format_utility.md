---
title: "Ext2 format utility"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Whitebread1 on 2006-10-30
This question isn't specifically about linux, but I don't know where else to ask.  I need to change my storage drives over to Ext2 and I need to do it while booted into windows.  Does anyone know of a free utility that can format some drives with the xt2 file system?  Thank you.

---

### Post by anaconda on 2006-10-30
Dont know any windows programs for that, but in linux (terminal ) just write 
sudo mke2fs /dev/sda2
and ofcourse change the /dev/sda2 to be whatever partition you want to format.. dont make a mistake here, because you might end up formatting wrong partition..

and if you use the -j option this will make it ext3 fs.. 

But maybe it is easier to boot with ubuntu liveCD and go to qtparted (or was it gtparted?) and do it graphically. just delete the partition you want to reformat, create a new partition, and make it ext2...

---

### Post by insub2 on 2006-10-30
> **Whitebread1 said:**
> This question isn't specifically about linux, but I don't know where else to ask.  I need to change my storage drives over to Ext2 and I need to do it while booted into windows.  Does anyone know of a free utility that can format some drives with the xt2 file system?  Thank you.

why do you need to do it while booted into windows?  do you mean you don't want to install linux?  Or do you absolutely need to be booted in windows?

i'm not sure if this will help for your situation, but i think i'd use a [Gperted livecd]("http://gparted.sourceforge.net/livecd.php") to format the partitions.


maybe this will help you:  [http://www.fs-driver.org/]("http://www.fs-driver.org/") (it's a program that mounts your Ext2/3 partition in windows.  gives it a drive letter and everything)

---

