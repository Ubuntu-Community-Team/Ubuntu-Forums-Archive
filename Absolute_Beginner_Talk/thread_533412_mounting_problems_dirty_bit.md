---
title: "mounting problems dirty bit"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2007-08-23
I was in the process of installing server03, but it didn't go so well. So I had to kill the installation. Currently, I do not have any windows OS installed on this machine. I would still like to access sda8 as it is a share for other windows PCs on my network. But currently I can't mount it on this OS and so I can't access it via a windows PC.
```
antsvr@ubuntu:~/mount$ sudo mount -t ntfs-3g /dev/sda8 /home/antsvr/mount/sda8
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda8': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
antsvr@ubuntu:~/mount$ 

```How do I reset the damn dirty bit without running check disk or installing windows?

btw ntfsfix doesn't seem to have a fix for this

```
antsvr@ubuntu:~/mount$ sudo ntfsresize -fi /dev/sda8
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name        : /dev/sda8
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 52427899392 bytes (52428 MB)
Current device size: 52427902464 bytes (52428 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 70 MB (0.1%)
Collecting resizing constraints ...
You might resize at 69177344 bytes or 70 MB (freeing 52358 MB).
Please make a test run using both the -n and -s options before real resizing!
antsvr@ubuntu:~/mount$ sudo mount -t ntfs-3g /dev/sda8 /home/antsvr/mount/sda8
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda8': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.
antsvr@ubuntu:~/mount$ 

```Advice?

---

### Post by moffa on 2007-08-23
Copy & Paste from the NTFS-3g forum:

Hi,

You can safely ignore the warning. If you want it to go away then you must
boot Windows. If you don't have Windows then don't bother about the
message, it's completely harmless.

Ntfs-3g can never cause the reason for this message. Some softwares which
can are ntfsfix and ntfsresize. But it's just a extra safety measure, it
doesn't mean that anything would be wrong with your partition. 

(szaka, Lead Developer)

[http://forum.ntfs-3g.org/viewtopic.php?t=532](http://forum.ntfs-3g.org/viewtopic.php?t=532)

---

### Post by ant2ne on 2007-08-25
sure I can safely ignore this warning, but I can't mount these drives/partitions. I intended to share them with the Windows Machines on my network. I can't share, what I can't mount. Since I don't have a windows OS on this machine, I can't even run scandisk. Grrr

---

### Post by asmoore82 on 2007-08-25
> **ant2ne said:**
> sure I can safely ignore this warning, but I can't mount these drives/partitions. I intended to share them with the Windows Machines on my network. I can't share, what I can't mount. **Since I don't have a windows OS on this machine**, I can't even run scandisk. Grrr

the only conceivable reason to use NTFS is so a local Windoze can read/write it ...

if no Windoze; I think it's time to reformat either ext3 or reiserfs.

---

### Post by ant2ne on 2007-08-25
> **asmoore82 said:**
> the only conceivable reason to use NTFS is so a local Windoze can read/write it ...

if no Windoze; I think it's time to reformat either ext3 or reiserfs.My goal is a file server for network windoze machines to read / write to

---

### Post by asmoore82 on 2007-08-25
> **ant2ne said:**
> My goal is a file server for network windoze machines to read / write to

NTFS is completely unneccessary. You do not need it to share files with Windoze over a network.
And obviously IT is causing problems where it is not needed. Eliminate the problem. :D

---

### Post by ant2ne on 2007-08-26
Interesting, the windows machines can access ext3 when it is shared, but not when local. I learned something! =) I was interested in toying with permissions between linux and windows machines.

---

### Post by MaxAxe on 2007-08-27
I have the exact same problem with my system too. Other than the fact that my drives had a windows XP installation earlier which was formatted to make way for Ubuntu. Now I can mount my NTFS partitions in read only mode. otherwise I get the same error message as mentioned in the 1st post ............

I have nother drive which is being taken from another system but that too can not be mounted. 

I want to keep the NTFS partition so that I can move the drive around if the need be and take data from windows based systems. 

Is there a solution ?

---

### Post by ellgor on 2007-08-27
Hi,

You could try this, while trying to set up a second hard drive and getting nowhere fast ( tried all sorts of tips etc ) I found that Disk Manager ( System-Admin-Disks ) can mount a disk or format one with a few simple clicks. 
On the left side are all devices connected with the options over to the right, clicking on a device highlights the options, I found that clicking on the partion tab gave me what I'd been trying all day to do, so give it shot, ok.

Regards, Ellgor

---

### Post by MaxAxe on 2007-08-30
^^ ............ Again .......... I cant find a System>>Administration>>Disks               I dont have anything that says disks .... is there something that I need to install ? .....  I do have the gnome partition editor  NTFS-3G tool, kwickdisk ..... installed .... what am I missing ,.... and is there a way to format a partition to NTFS so that a windows system would read it ... ??? :confused:

---

### Post by ant2ne on 2007-08-30
I didn't solve this problem. I ended up reformatting the NTFS volumes int ext3, and then formatting again to NTFS. of course, this wont work if you need data from these devices. Could you back up the data by booting from another OS like bartsPE or UBCD4WIN, a boot able USB or something similar?

---

