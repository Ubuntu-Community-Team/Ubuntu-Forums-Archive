---
title: "Can Ubuntu use NTFS?"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by Mebailey on 2005-12-21
I am using XP, I have a hard drive for the OS, and a separate one for files etc.

I am hoping to dedicate a hard drive to Ubuntu, and be able to operate both XP and Ubuntu as required, with both utilising the same drive for my files.

Does anyone have any opinions as to whether this will be possible. I've had a go at the online OS and it seems to pick up where Atari left off in terms of operation, which I like. I'm just wary of not being able to run Windows when I need to.

Thanks for your time


Michael

---

### Post by jbmalone on 2005-12-21
It can read NTFS, but it cannot write to it.

---

### Post by Mebailey on 2005-12-21
Do you know what file system it does use, and if Windows can read and write to *it[I]?*[/I]

---

### Post by zerohalo on 2005-12-21
Michael, you can run both XP and Ubuntu as a dual-boot without problems. Of course it does mean rebooting your computer when you want to do something in Windows. (Alternatively you could run Windows as a VM inside Ubuntu, but that requires purchasing a program like VMWare, so you might not want to do that.)

If you want XP and Ubuntu to access the same data (both read and write), then you need to format the partition with your data as Fat32, not NTFS. I recommend you set up 3 partitions: One for your XP OS, another for your Ubuntu OS, and another for your data, which would be accessible by both systems (and which you could mount as your "home" folder in Ubuntu).

---

### Post by paulmilliken on 2005-12-21
[QUOTE=Mebailey]Do you know what file system it does use, and if Windows can read and write to *it[I]?*[/I][/QUOTE]
Ubuntu uses ext2 or ext3.  If you want a shared drive to be readable and writeable by both windows and Ubuntu then consider using a FAT format.

Paul

---

### Post by Rinzwind on 2005-12-21
Kernel 2.6 can (sort of).

[http://bisqwit.iki.fi/story/howto/ntfs/](http://bisqwit.iki.fi/story/howto/ntfs/)

---

### Post by Mebailey on 2005-12-21
I'm afraid I know little about the actual "mechanics" of FAT32 and NTFS except their names, do you know if there what the advantages of using one over another are. 

For example, am I likely to have any problems or reduced performance using FAT32 instead of NTFS?

---

### Post by towsonu2003 on 2005-12-21
For your dual booting concerns, this might be helpful: 
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

for filesystems and comparison (not too much though) this could help: [http://en.wikipedia.org/wiki/FAT32#Future](http://en.wikipedia.org/wiki/FAT32#Future)

and I quote from above link: > For most purposes, the NTFS file system that was developed for the Windows NT line is superior to FAT from the points of view of efficiency, performance and reliability; its main drawbacks are the size overhead for small volumes and the very limited support by anything other than the NT-based versions of Windows, since the exact specification is a trade secret of Microsoft, which in turn makes it difficult to use a DOS floppy for recovery purposes. Microsoft provided a recovery console to work around this issue, but they severely limited what could be done through it for security reasons.

and > The FAT32 **formatting** support in Windows 2000 and XP is limited to drives of 32 gigabytes, which effectively forces users of modern hard drives either to use NTFS or to format the drive using other tools outside Windows. A workaround to this involves using a version of mkdosfs that has been ported from Linux to Windows.

I don't see any performance issues myself (have windows in 20GB NTFS, Ubuntu in 20GB ext3, /home in 20GB ext3, and a 1GB Windows-Ubuntu share as FAT32 for transferring files).

---

### Post by Alpha_toxic on 2005-12-21
One more option:
You may actually have only EXT3 and NTFS drives as linux can read from NTFS and there are tools that let you read/write from Win to EXT3.

For example [http://www.fs-driver.org]("http://www.fs-driver.org")

This way you can have an EXT3 partition for use for both Win and Linux and a small NTFS for the Windows install and the programs only~5-10GB.

Note that I haven't actually tried it cause this program does not support my win (2003). But it should be fine for 98/NT/2000/XP, well everything else...

---

