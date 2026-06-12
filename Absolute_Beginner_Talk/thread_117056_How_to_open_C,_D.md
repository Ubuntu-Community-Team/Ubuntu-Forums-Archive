---
title: "How to open C:\, D:\"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by geniusvicks on 2006-01-14
I'm not sure how I did it but I managed to get by partitioner while installing Ubuntu.
I think I installed ubuntu in E:\ 
then now how do I open C:\ and D:\
My F:\ is missing even while using windows( I think I deleted the partition) how do I get that 10 gb of my F back. I have got a 40gb HD but I can use only 30GB form my C:\ D:\ and E:\

---

### Post by adwait on 2006-01-14
The partition that is used by Linux will not be visible in Windows because of incompatibility of Windows with all other file systems except its own.

---

### Post by public_void on 2006-01-14
It should show in Control Panel (thats in Classic view)-->Administrative Tools-->Computer Management and under disk Management. It should show your partitions, your linux partitions won't have names, but will be "healthy(Unknown partition)". But you can't access them, just know they're there

---

### Post by rubinstein on 2006-01-14
[QUOTE=geniusvicks]I'm not sure how I did it but I managed to get by partitioner while installing Ubuntu.
I think I installed ubuntu in E:\ 
then now how do I open C:\ and D:\[/QUOTE]
You mean when you are using Ubuntu how do you open C: and D:?
Partition names are different under Linux. You can read about it at [http://linux.org.mt/article/partnames](http://linux.org.mt/article/partnames)
It is likely that C: is /dev/hda1, and Ubuntu should have recognised it during installation and put hda1 on your desktop.

---

### Post by GMathews on 2006-01-14
You can mount your Windows (NTFS) Filesystem in Ubuntu. Just run a search for it and its also in the help file that comes with Breezy. However you can only read from your Windows Partition (ie C:) but not write onto it when in Linux

---

### Post by geniusvicks on 2006-01-14
[QUOTE=GMathews]You can mount your Windows (NTFS) Filesystem in Ubuntu. Just run a search for it and its also in the help file that comes with Breezy. However you can only read from your Windows Partition (ie C:) but not write onto it when in Linux[/QUOTE]
How do I write in Linux on my C: drive
When I open dev\hda1 i get the following error: Couldn't display "/dev/hda1".
How do I get my F:\ back?

---

### Post by Kamputer on 2006-01-14
[QUOTE=geniusvicks]How do I write in Linux on my C: drive
When I open dev\hda1 i get the following error: Couldn't display "/dev/hda1".
How do I get my F:\ back?[/QUOTE]

Put in /etc/fstab something like */dev/hda1 /media/diskC ntfs umask=555 0 0*, but do not forget to replace spaces with tabs and to create /media/diskC. Read this before - [http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html"). Better not try to write in your NTFS partition from Linux.

---

### Post by Kimm on 2006-01-14
> 
How do I write in Linux on my C: drive
When I open dev\hda1 i get the following error: Couldn't display "/dev/hda1".
How do I get my F:\ back?


As noted earlier, pathnames are different in Linux, but to access your harddrive you dont want the path /dev/hda1 and absolutely not \dev\hda1

Your primary partion is /, and thats it, try navigating to: / not \!

your other harddrive may be something lik /media/windows, but I dont know.

---

### Post by aysiu on 2006-01-14
To mount your Windows partitions, see the fourth link of my signature.
The terminal is in Applications > Accessories > Terminal
That's where you copy and paste commands.

---

### Post by geniusvicks on 2006-01-14
How do I get my 10 GB of space back?
My HD is 40 GB while installing I screwed up in partition table and forgot to do something to my last partition and it has disappeared. (I'm using dual OS) When I open windoze I cant access my F drive.
How do I make partitions other than C:\drive to convert to linux file system?

---

### Post by cwaldbieser on 2006-01-14
[QUOTE=geniusvicks]How do I get my 10 GB of space back?
My HD is 40 GB while installing I screwed up in partition table and forgot to do something to my last partition and it has disappeared. (I'm using dual OS) When I open windoze I cant access my F drive.
How do I make partitions other than C:\drive to convert to linux file system?[/QUOTE]
You use a program like "cfdisk" to format the partition with a filesystem that is usable by Ubuntu.  If you want to use the space for both Windows and Ubuntu, you should make it a fat32 filesystem.  If you just want it for Ubuntu, ext3 is probably a good choice.  Be careful, because you can accidently format a partition you didn't want to, and there is no easy way to recover!

After you format the partition, you modify the filesystem table, /etc/fstab.  This has entries in it that tell where different partitions get mounted in your filesystem.  Some of the links provided probably already explain that concept.

---

