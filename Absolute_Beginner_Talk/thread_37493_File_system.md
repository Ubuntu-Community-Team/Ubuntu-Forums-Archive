---
title: "File system"
date: 2005-05-27
forum: Absolute Beginner Talk
---

### Post by Hansje on 2005-05-27
I'm ready to install a Linux, first I thought Knoppix, but Ubuntu is much better i found out with the life cd. I want to format a partition for ubuntu, but what is the best file system? And if it is possible, a file system that windows can read. and my last question: can ubuntu read NTFS?

Greetz
Hansje

---

### Post by f.prisson on 2005-05-27
> I want to format a partition for ubuntu, but what is the best file system? You'll find different opinions about this topic, but I think for a desktop system there's not much difference between them.

> And if it is possible, a file system that windows can read I don't think that's possible> can ubuntu read NTFS? yes, it can

---

### Post by Hansje on 2005-05-27
But I can't install Ubuntu on a NTFS partition? 
FAT maybe?

Greetz
Hansje

---

### Post by tread on 2005-05-27
Installing Linux on a FAT filesystem wouldn't work, since FAT does not support permissions.

---

### Post by f.prisson on 2005-05-27
No way to install it on NTFS because no write support. You may be able to install it on FAT32 if you preformat it, but I don't recommend this, because FAT32 is an old Microsoft format without journal, even Microsoft replaced it with NTFS.

I would create an extra partion with FAT for file swapping purposes.

---

### Post by f.prisson on 2005-05-27
> Installing Linux on a FAT filesystem wouldn't work, since FAT does not support permissions Thought only about write support, didn't thought about that, you're right.

---

### Post by Moobert on 2005-05-27
ext3 and ext2 can be read by this tool on windows:

[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
but you do need to export files before you can use them.

ext2 can be mounted in windows by:

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)
never had much luck with it...

I'd go for ext3 myself due to the file system journaling and lack of needing to defragment.

---

### Post by Kyral on 2005-05-27
Actually, according to the UbuntuGuide, there IS a program for Windows that allows you to read ext2/ext3 partitions

[http://www.ubuntuguide.org/#readlinuxpartitionsinwindows](http://www.ubuntuguide.org/#readlinuxpartitionsinwindows)

And NTFS read support is in the kernel. So there you go. Just make a new part and choose ext3

---

### Post by N'Jal on 2005-05-27
Personally right now i use EXT3 but will be moving over to ReiserFS as since i used Suse i have found that to perform that little bit better on my hardware, but that's just my PC

---

### Post by maspro on 2005-05-27
Normally you can only read on NTFS partitions under linux, but read/write access seems to be possible with certain risks:

check the following links:
[http://linux-ntfs.sourceforge.net/](http://linux-ntfs.sourceforge.net/)
[http://freshmeat.net/projects/linuxntfs/](http://freshmeat.net/projects/linuxntfs/)
[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

 :smile:

---

### Post by Hansje on 2005-05-28
[QUOTE=maspro]Normally you can only read on NTFS partitions under linux, but read/write access seems to be possible with certain risks:

check the following links:
[http://linux-ntfs.sourceforge.net/](http://linux-ntfs.sourceforge.net/)
[http://freshmeat.net/projects/linuxntfs/](http://freshmeat.net/projects/linuxntfs/)
[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

 :smile:[/QUOTE]
 Amazing, so many helpers, but it is clear, i will use the ext3 file system

Thanks
Hansje

---

