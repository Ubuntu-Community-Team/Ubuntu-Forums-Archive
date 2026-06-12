---
title: "advantage of /boot partition?"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-23
what is the advantage of a seperate /boot partition?

---

### Post by Sef on 2006-05-23
> what is the advantage of a seperate /boot partition?

If you use XFS or JFS, then you can use them if you do a boot partition.  Otherwise GRUB will fail to install.

---

### Post by user1397 on 2006-05-23
[quote=Sef]If you use XFS or JFS, then you can use them if you do a boot partition.  Otherwise GRUB will fail to install.[/quote]
so XFS and JFS are boot managers?

---

### Post by Sef on 2006-05-23
> so XFS and JFS are boot managers?

No, they are file systems, like ext3 or reiserfs.

---

### Post by user1397 on 2006-05-23
[quote=Sef]No, they are file systems, like ext3 or reiserfs.[/quote]
oh
so if i want grub, i shouldnt bother with a /boot partition? (srry for being repetitive, but i just want to be sure)

---

### Post by Mustard on 2006-05-23
I think the answer is that grub needs an ext2 file system to install itself (ext3 is basically just ext2 with journals).  If your file system is such that grub can't install to it, then grub will fail.  You could however have a /boot partition formated in ext2 while the rest of your file system uses some other format ie XFS or JFS.  I'm just surmising this from what Sef has already stated. :)

---

### Post by xXx 0wn3d xXx on 2006-05-23
[QUOTE=erik1397]oh
so if i want grub, i shouldnt bother with a /boot partition? (srry for being repetitive, but i just want to be sure)[/QUOTE]
Well, if you are going to use XFS or JFS (both are high performance file systems) then you want a seperate /boot partition. Although, when I use XFS for my partitions with a seperate /boot partition, grub still failed to install.

---

### Post by catlett on 2006-05-23
Sorry to jump in but I wanted to do a fresh install and was going to set up whatever partitioning was optimal. I was thinking of posting about a boot partition anmd saw this post on first entry and thought I would jump in. 
So you only need  a boot partition  if the filesystem is one Grub cannot install to? If the file system is xfs or jfs you need an ext2  (or Fat, is that acceptable?) to install grub to or grub will not be usable as a bootloader?
Does this then mean a boot partition is unnecessary if your file system is Grub compatable  i.e. ext2 ?
Is it good to put grub in a boot partition if you have multiple operating systems installed to many partitions?
Is one filesystem better than another for grub to install on?
What is the size requirement if you are going to make a boot partition and install grub to it?

---

### Post by Mustard on 2006-05-23
I've been reading over this link trying to work it all out, as I wasnt too sure about the ext2 only information I gave.  At the moment I'm back to having no clue what it is going on. :)

[http://www.gnu.org/software/grub/manual/grub.html#Images](http://www.gnu.org/software/grub/manual/grub.html#Images)

What confuses me with this question is that the link I am reading seems to say that it will support many more filesystems including XFS and JFS..

[quote=website]Support multiple filesystem types
    Support multiple filesystem types transparently, plus a useful explicit blocklist notation. The currently supported filesystem types are BSD FFS, DOS FAT16 and FAT32, Minix fs, Linux ext2fs, ReiserFS, JFS, XFS, and VSTa fs. See Filesystem, for more information. [/quote]

---

### Post by catlett on 2006-05-23
[QUOTE=Mustard]I've been reading over this link trying to work it all out, as I wasnt too sure about the ext2 only information I gave.  At the moment I'm back to having no clue what it is going on. :)

[http://www.gnu.org/software/grub/manual/grub.html#Images](http://www.gnu.org/software/grub/manual/grub.html#Images)[/QUOTE]
You have to respect an honest man:)

---

### Post by confused57 on 2006-05-23
I don't think there is any advantage to a separate boot partition, but some systems require it, see this:

[http://wiki.linuxquestions.org/wiki/GRUB#Error_18](http://wiki.linuxquestions.org/wiki/GRUB#Error_18)

I found it attempting to answer a post a few hours back with "error 18" in the title.

---

### Post by Mustard on 2006-05-23
To add to the mystery I am reading another guide to Grub that doesnt list XFS and JFS as supported filesystems..

[quote=someguide]Support multiple filesystem types
    Support multiple filesystem types transparently, plus a useful explicit blocklist notation. The currently supported filesystem types are BSD FFS, DOS FAT16 and FAT32, Minix fs, Linux ext2fs, ReiserFS, and VSTa fs. See section Filesystem syntax and semantics, for more information.[/quote]

I think it could be an issue of what version of grub is being used.  Perhaps the latest version of Grub does support XFS and JFS, but previous versions haven't.  I'm still looking into it atm. :)

-edit-

I've just noticed that Breezy is using 0.95 and Dapper is using 0.97, so I assume that XFS and JFS support is not in the earlier version for breezy.

-edit2-

Well that theory didn't pan out.  Seems XFS support has been in grub for quite some time.  Ah well, I'm going cross-eyed reading all these changelogs and manuals and its all a bit offtopic anyway.

---

### Post by catlett on 2006-05-23
You're not going of topic exactly, it's about boot partitions and these days it means grub(how many use the linux loader anyways?). This is a thread gone  and on and on and on:-D [http://forums.gentoo.org/viewtopic-t-383320.html](http://forums.gentoo.org/viewtopic-t-383320.html)

---

### Post by user1397 on 2006-05-24
All i can say is, i wont install a seperate boot partiton next time i partition my hard drive.  ill just have a / partiton, a /home partiton, and good 'ol swap.

---

### Post by skippy81 on 2006-05-24
I have a 500mb ext3 /boot partition, a 7gb XFS root partition and the rest of my space is used for my /home (also XFS).   

As mentioned above, Grub will not install to an XFS partiton. 

I can't say that there is any major advantage of having a seperate boot partition, but then again, it doenst take long to set one up.  Having a seperate home partition is VERY handy however.

---

### Post by user1397 on 2006-05-24
[quote=skippy81]I have a 500mb ext3 /boot partition, a 7gb XFS root partition and the rest of my space is used for my /home (also XFS).   

As mentioned above, Grub will not install to an XFS partiton. 

I can't say that there is any major advantage of having a seperate boot partition, but then again, it doenst take long to set one up.  Having a seperate home partition is VERY handy however.[/quote]
i agree, having a /home partition is very handy, cause you can upgrade to the next version quickly and easily, w/o risking the loss of data or configurations (at least as i have learned; too bad i installed ubuntu the default way, and therefore all i have is a / partition and swap:()
So whats the advantage of a /root partition? (like i see you have, skippy81:))

---

### Post by ekerazha on 2006-08-12
JFS is perfectly bootable... only XFS has problems.

---

### Post by tmetro on 2006-11-19
> **erik1397 said:**
> what is the advantage of a seperate /boot partition?

There are a number of reasons why you might want or need a separate /boot partition, some historical and some still relevant.

[LIST]
[*]Boot loader file system limitations
This has already been mentioned above.

[*]Non-bootable file system, like RAID used for root
Similar to the first item. Sometimes if RAID is used for root, /boot will be placed on a separate partition, and optionally mirrored using rsync or other non-RAID method.

[*]Cylinder addressing limits in BIOS or boot loader
This was the primary motivation for a separate boot partition in the past. The BIOS on some machines can't address the cylinders beyond certain thresholds, and some boot loaders have this problem too. The workaround was to put the kernel into a partition at the front of the disk. Some discussion of this in the [wiki]("https://wiki.ubuntu.com/WartyWarthogInstallNotes?highlight=%28%2Fboot%29"). 

[*]Rescue kernel file system limitation
After a failed kernel upgrade, it'd be nice to be able to access your /boot partition to rename or replace the kernel. To do so, your rescue kernel needs to support the file system. Live CDs, with space to store modules for most file systems, have made this less of an issue.

[*]Extra protection against partition table corruption
The rarely ever accessed /boot partition is less likely to get trashed, though if your root partition gets trashed you still might not be able to do much to fix the system without using a bootable rescue disk. Again, Live CDs make this not much of an advantage.
[/LIST]

 -Tom

---

