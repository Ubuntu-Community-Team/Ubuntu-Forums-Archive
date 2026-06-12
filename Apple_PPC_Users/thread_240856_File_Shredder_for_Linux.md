---
title: "File Shredder for Linux?"
date: 2006-08-21
forum: Apple PPC Users
---

### Post by andy_fac51 on 2006-08-21
When my Ubuntu and Kubuntu CD's came in the mail several weeks ago I thought I was dumping Windows XP forever. However, after updating the security packages, (I was using Ubuntu at the time)downloading WINE etc. I discovered two things. No. 1 the Wine package I downloaded did not show up under "office", and I also noticed that the files I was deleting were not being securely "deleted." 
To remidy this problem, I decided to look for a file shredder that could be used in Ubuntu/ Kubuntu, I could find no such program. My question to people in the Linux community is this: if Linux is so "secure" then why is there not a Linux file shredder? (after all, when you "delete" a file it is not erased like file shredders do,the file is simply "Ignored" and remains on the hardrive for all to see when you get rid of your computer.) I would switch to Linux Ubuntu in a heartbeat if there was a file shredder for it, hands down. Unfortunately I had to switch back to Windows XP since it has file shredders written for it.
I would also like to add that if Linux is to ever Trump Windows completly, it needs to have a file shredder to prove once and for all that Linux is the most secure operating system. Is there a file shredder I can use for Linux?

---

### Post by bukwirm on 2006-08-21
Try the command 'shred'.

---

### Post by blackened on 2006-08-21
Optionally, you could write a Nautilus script for shred if you prefer using the GUI.

---

### Post by lupine_nickt on 2006-08-21
Or use wipe.

xF,

...Nick

---

### Post by calum on 2006-08-21
Be aware that the success of Linux file shredders is rather filesystem-dependent though... many such utilities(including shred, IIRC) won't work on journaled filesystems like ext3.  See [http://www.digg.com/linux_unix/LINUX:_Securely_deleting_files_with_shred](http://www.digg.com/linux_unix/LINUX:_Securely_deleting_files_with_shred) et al. for more info.

---

### Post by jargoman on 2007-06-09
this part of the man page explains that for ext3 shred doesn't work in data=journal mode, for shred to work you need to change /etc/fstab 

In  the  case  of  ext3 file systems, the above disclaimer applies (and
       shred is thus of limited  effectiveness)  only  in  data=journal  mode,
       which  journals  file  data  in addition to just metadata.  In both the
       data=ordered (default) and data=writeback modes, shred works as  usual.
       Ext3  journaling  modes  can  be  changed  by adding the data=something
       option to the mount  options  for  a  particular  file  system  in  the
       /etc/fstab file, as documented in the mount man page (man mount).
----------------------------------------------------------------------------------------

Does anyone know of a way to shred free space? Like you can in mcaffee file shredder for winblows.

Seeing how shred is rewriting in a new spot of free space each time in journal mode could I just shred a file over and over till it ultimatly shreds all free space?

---

### Post by jargoman on 2007-06-27
I have the solution if you want to shred free space. There is a program called scrub. This is the home page.

[http://www.llnl.gov/linux/scrub/](http://www.llnl.gov/linux/scrub/)

I couldn't find a .deb file for x86_64 arch so I downloaded the 1.9 source tarball. I also didn't find a read me file so I compiled and installed with...
$ make 
$ sudo mv scrub /usr/bin

I don't think any dependancies are needed. Just build-essential

here's how to shred free space

it should be noted that I have three ubuntu partitions and decided it only made sence to erase the free space on my /home partition.

$ scrub -X ~/erase_me_after

this will create a redundant file that has consumed all free space. You may see a warning like "100% space used on partition /home". After that you can simply remove erase_me_after or if your really paranoid and willing to let your computer run for an hour or so

$ shred -u ~/erase_me_after

I will offer a warning that writing a file using 100% of free space can have unexpected results. It might be a good idea to back up data first. I don't think it's that bad though because durring the process my laptop ran out of battery power and all is good. Also while this process is running you wont be able to save to that partition.

To shred free space on root filesystem. (I didn't try this but it will work)
$ sudo scrub -X /erase_me
$ sudo shred -u /erase_me

---

### Post by 3rdalbum on 2007-06-27
If you are concerned about the ability of malicious people to see your deleted data, what about the data you still have on your computer?

You should set up Bitlocker, to have an encrypted home partition. Even deleted files will still be in encrypted form on the disk. Ultra-secure.

---

### Post by eentonig on 2007-06-27
from 

> shred --help

> ...
CAUTION: Note that shred relies on a very important assumption:
that the file system overwrites data in place. This is the traditional
way to do things, but many modern file system designs do not satisfy this
assumption. The following are examples of file systems on which shred is
not effective, or is not guaranteed to be effective in all file system modes:

* log-structured or journalled file systems, such as those supplied with
  AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)

* file systems that write redundant data and carry on even if some writes
  fail, such as RAID-based file systems

* file systems that make snapshots, such as Network Appliance's NFS server

* file systems that cache in temporary locations, such as NFS
  version 3 clients

* compressed file systems
...


---

### Post by stuartbh on 2007-07-11
To whom it shall concern or can answer the instant query:

I understand that Feisty Fawn (7.04 Ubuntu) has recently become available in a live/bootable version for the PPC architecture (say for a PowerBook 1.5).

Is schred or any other such file shredder inclusive to this 7.04 PPC edition?

If so, how can I use Ubuntu 7.04, if I wish to fully erase a drive that had MacOS based stuff on it?

I am not object to reformatting the drive as EXT2 if that is what is requisite to do this, is it?

Is that the most effective way to do this, or is DBAN available on 7.04 PPC?


V/R,

Stuart B. Tener, N3GWG
Beverly Hills, CA / Las Vegas, NV / Washington, DC / Philadelphia, PA

---

### Post by 3rdalbum on 2007-07-12
Do you want to securely delete all the data from the Mac OS drive?

If so, you can use Drive Setup on OS X to "Write Zeroes" to the disk, and then use the Debian Installer on Ubuntu to set up full drive encryption.

---

