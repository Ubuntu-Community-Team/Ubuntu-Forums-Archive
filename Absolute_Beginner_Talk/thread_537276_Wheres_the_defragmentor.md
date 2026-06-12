---
title: "Wheres the defragmentor?"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by MobileDev on 2007-08-28
Here I am, back in the beginner forum because I don't know where to post this question. GPartED is a great partition editor and I have it installed on my computer (running Xubuntu 7.04, Fiesty). I know it's great for it's intended purpose, but does it defrag disks as well? If not, does anyone know of a good disk defrag program for Linux that handles both Windows and Linux file systems? I need support for FAT16, FAT32, NTFS, ext2, ext3, and ReiserFS  file systems

---

### Post by Steveway on 2007-08-28
Linux Filesystems don't normaly need to be defraged.
They are build so that they only start to fragment if they are about 95% full.
I don't think that there are any defraggers on Linux for Windowsfilsystem, mostly because we don't need them.
EDIT: Haha first and best answer!

---

### Post by MetalMusicAddict on 2007-08-28
It's generally accepted that in linux you dont need to defrag. Search the forum next time and you''ll see. ;)

---

### Post by stinger30au on 2007-08-28
linux does not need a defragmenter on its native partitions.

the fat32/ntfs stuff may do.

---

### Post by bodhi.zazen on 2007-08-28
LOL

Here are some links if you would like the gory details :

	[http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html](http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html)
	[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)
	[http://www.linuxquestions.org/questions/showthread.php?t=55710](http://www.linuxquestions.org/questions/showthread.php?t=55710)

	Ext3 : [http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

---

### Post by slouck on 2007-08-28
Great information bodhi!  I love to see informative posts like this.  I do think the OP had a good idea asking about a linux utility that can defragment a windows filesystem even if linux doesnt itself require it.  It would make linux live/recovery cd's that much more powerful themselves. Now that ntfs-3g is gaining momentum I expect to see some applications start to creep into this space(even commercial).  Maybe even a mega utility that can defrag deworm and scan for virii.  Thoughts?

---

### Post by bodhi.zazen on 2007-08-28
> **slouck said:**
> Great information bodhi!  I love to see informative posts like this.  I do think the OP had a good idea asking about a linux utility that can defragment a windows filesystem even if linux doesnt itself require it.  It would make linux live/recovery cd's that much more powerful themselves. Now that ntfs-3g is gaining momentum I expect to see some applications start to creep into this space(even commercial).  Maybe even a mega utility that can defrag deworm and scan for virii.  Thoughts?

he he he ... a lot of those problems see to have gone away now that I do not use ntfs :twisted:

There are some very capable tools out there, one of which is knoppix (often over looked).

You might also like TestDisk : [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

And tools like Clonezilla : [http://clonezilla.sourceforge.net/gparted-clonezilla/](http://clonezilla.sourceforge.net/gparted-clonezilla/)

---

### Post by LaRoza on 2007-08-28
> **slouck said:**
> Great information bodhi!  I love to see informative posts like this.  I do think the OP had a good idea asking about a linux utility that can defragment a windows filesystem even if linux doesnt itself require it.  It would make linux live/recovery cd's that much more powerful themselves. Now that ntfs-3g is gaining momentum I expect to see some applications start to creep into this space(even commercial).  Maybe even a mega utility that can defrag deworm and scan for virii.  Thoughts?

There is a program to defragment FAT32, it is called "defrag" I believe. "sudo aptitude install defrag".

---

### Post by MobileDev on 2007-08-29
Thanks for the info! First of all, since ext2/3 does not require defragmentation, that still leaves my external USB hard drive, which is currently serving a very important purpose. You see, I still don't have internet, so I have to take my hard drive back and forth to the library if I want great open source software. I took a look at that defrag program, but it only does  minix, xiafs, and ext2 filesystems and I don't have admin rights on library computers. Lately, I've noticed a decrease in speed when installing from my external hard drive, and it's getting worse. I tried the fsck command on the two FAT32 partitions and it says that my sda1, known as E:\ on windows, is 23% fragmented. This is the partition I use the most, so it kind of makes sense, but is there a way to fix this problem without reformatting the partition? I do have plenty of disk space inside the computer to do it, but I'd rather not spend an hour doing that.

OTSN (Off Topic Side Note): USB drive access in general is slow. Does Xubuntu support USB 2.0? If so, how can I enable it by default, or set it to auto-detect what the device is capable of using?

---

### Post by biomedtech on 2007-08-30
Is there a query that will tell me what the percentage of fragmentation is?  When entering the fsck command, I am warned that 'SEVERE damage may occur, and am I sure I know what I am doing?'

I don't want to change anything, I'm only curious what fragment percentage is. I abort at that point.

---

### Post by MobileDev on 2007-09-12
When anything Linux related says "SEVERE damage may occur", you generally have a 60/40 shot of ruining your system. But then again, what do I know, I've only been distro hopping two years.

---

### Post by sumguy231 on 2007-09-12
fsck is probably telling you "SEVERE damage may occur" because you're trying to run it on a mounted partition. Unmount the device first, then run fsck.

> Does Xubuntu support USB 2.0?
Yep.

---

