---
title: "Ubuntu and Win"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by BarFly on 2006-12-07
I am dual booting Ubuntu and XP.  XP is on a small HDD, while Ubuntu is on a large one.  If I want to share files between the two OS's, do I partition the large Ubuntu drive to add a FAT32 section?  I need to do this because Linux does not have an equivalent of a program that I need for work.  Will both OS's recognize the FAT32 partition?

Can someone walk me through this?

Thanks, buddies.

---

### Post by yabbadabbadont on 2006-12-07
If you have free space on either drive, you should be able to create a fat32 partition.  Both Windows and Linux should have no problems reading and writing to a fat32 partition.  In fact, that is usually the easiest way to move files back and forth between them.  (on the same machine that is)

---

### Post by Old Pink on 2006-12-07
Boot from a Live CD of Ubuntu. When you see the desktop, click "System > Administration > GNOME Partition Editor"

This gives you a simple GUI to let you move your partitions around :)

---

### Post by meng on 2006-12-07
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

---

### Post by Hendrixski on 2006-12-07
Have you looked at Wine as an option?  it can run a ton of Windows applications.  Not all of them well, to be honest.  There's a commercial version of wine from Codeweaver called Crossover.  Plus many of the file formats for windows applications have been reverse engineered to work on LINUX applications, like openOffice. :)


If you need to share information between partitions you don't need to create a new one (though that is one way of doing it), there are tools for writing between them as well such as ntfs-38,(though these tools will not protect you from yourself, if you delete a windows registry file your windows will be hosed).  Try the directions on  [http://www.arsgeek.com/?p=585](http://www.arsgeek.com/?p=585)
or
[http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html).
or
[http://ubuntuos.wordpress.com/2006/08/02/howto-write-to-windows-ntfs-drive-from-ubuntu-ntfs-3g/](http://ubuntuos.wordpress.com/2006/08/02/howto-write-to-windows-ntfs-drive-from-ubuntu-ntfs-3g/)
or [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) 


Something I've been looking into trying is running my windows partition from Linux in a virtual machine, like Xen, or VMWare.  Because then I would be essentially running both operating systems at once.  Although I haven't tried it yet, so don't know if I should recommend it or not.  I assume it's really slow.

---

### Post by ub-into on 2006-12-10
I used the 30-day trial of VmWare in both Ubuntu and SuSE, and as long as I allocated enough of my RAM to the VM, it ran at near native speed (at least for document processing, OCR processing, and the like).  However, I also tried Parallels Workstation (MUCH cheaper at around $50 compared to nearly $200 for VmWare), and I actually thought it ran even better than VmWare did (less resource usage by far, for example).  However, the problem of getting at NTFS directories still remains, since a virtualized Windows would be trying to access NTFS files through the action of the Linux filesystem acting in-between.  What WAS really nice, though, was the ability to use some of my Windows end-user apps (like Scansoft Omnipage, for instance) on my Linux files.

Let me know if you have any questions about this ... I will try to answer them as best as I can ... (not a programmer ... just a 'power-user-lite', i guess !)

---

### Post by daou on 2006-12-10
VmWare has been free since last summer I believe.

[HowTo: Windows (XP) on Ubuntu with VMWare Server]("http://www.ubuntuforums.org/showthread.php?t=183209").

Another option is to install a program that is able to read and write to NTFS partitions (Ubuntu can already read NTFS). There were some bugs initially with writing to NTFS but these have been ironed out for a while now.

Or you could install ext3 support to your Windows. Many possibilities.

---

