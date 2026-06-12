---
title: "reiserfs, or ext3?"
date: 2008-04-23
forum: Arch and derivatives
---

### Post by chucky chuckaluck on 2008-04-23
going for it (installing arch) on friday. i had reiserfs installed when i briefly flirted with sidux. i didn't last long enough with sidux (don't remember why. no patience probably) so i didn't really get to see what reiser was all about. well?

---

### Post by fwojciec on 2008-04-23
> **chucky chuckaluck said:**
> going for it (installing arch) on friday. i had reiserfs installed when i briefly flirted with sidux. i didn't last long enough with sidux (don't remember why. no patience probably) so i didn't really get to see what reiser was all about. well?

I'd say reiserfs - it's particularly useful in Arch considering that pacman database uses the filesystem and huge number of small files.  Ext3 is usually fine, but reiserfs is going to be perceptibly faster, especially in Arch.  If you're making separate root and home partitions I'd say make root reiserfs and home ext3 with "journal_data" -- see this [wiki article]("http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips") on how to set it up and what are the benefits.

Also, if you decide to use reiserfs, I'd suggest adding "resierfs" to the module line of /etc/mkinitcpio.conf during installation so it looks something like this:
```
MODULES="pata_amd ata_generic sata_nv reiserfs"
```
Some of the modules that the installer will put there by default might be different -- it depends on whether you use Intel or AMD.  Having "reiserfs" in there basically makes sure that the reiserfs module is always written to the kernel boot image whenever you update the kernel.  It really shouldn't be necessary, but it won't hurt and could save you some kernel panic issues in the future.

---

### Post by Gigamo on 2008-04-23
Myself I'm using ext3 on / and jfs on /home and /storage.

I really like JFS.

---

### Post by ShodanjoDM on 2008-04-23
Maybe [**_[COLOR="DarkRed"]this[/COLOR]_**]("http://www.debian-administration.org/articles/388") will help you decide

---

### Post by MisfitI38 on 2008-04-23
For best pacman performance and most perceivable difference, make /var the first partition (its own separate partition e.g.: sda1) and use JFS or ReiserFs. 
(Keep it on the fast edge of the disk and use a high performance FS. My .02 :) )

---

### Post by Barrucadu on 2008-04-23
I am using Ext3, though I've been considering switching to XFS after seeing a few benchmarks. I was using Ext3 also on the drive containing my movies, but I changed that to JFS and definitely noticed a difference in speed with opening and copying files.

---

### Post by articpenguin on 2008-04-23
I use JFS and ext3. I use jfs for / cuz it is faster and ext3 for /home where personal data matters.

---

### Post by MisfitI38 on 2008-04-23
> **Barrucadu said:**
> I am using Ext3, though I've been considering switching to XFS after seeing a few benchmarks. I was using Ext3 also on the drive containing my movies, but I changed that to JFS and definitely noticed a difference in speed with opening and copying files.

Just make sure you do NOT use XFS on /var. XFS performs poorly in conjunction with large numbers of small files, like the ones created under /var on Arch.

---

### Post by chucky chuckaluck on 2008-04-23
well, i was hoping for a one file system answer (i should have known :rolleyes:). to be perfectly candid, i really haven't understood half of what you guys are saying. so, with that in mind, if i were to pick one file system for the whole mess, given that i'm pretty much of a minimalist end user, what would you all pick for me? 

btw, i do appreciate the in depth responses, even if they're currently over my head.

---

### Post by articpenguin on 2008-04-23
> **chucky chuckaluck said:**
> well, i was hoping for a one file system answer (i should have known :rolleyes:). to be perfectly candid, i really haven't understood half of what you guys are saying. so, with that in mind, if i were to pick one file system for the whole mess, given that i'm pretty much of a minimalist end user, what would you all pick for me? 

btw, i do appreciate the in depth responses, even if they're currently over my head.

to make it short and simple use ext3. Avoid Reiserfs and xfs.

[http://linuxmafia.com/faq/Filesystems/reiserfs.html](http://linuxmafia.com/faq/Filesystems/reiserfs.html)

---

### Post by Simpatico on 2008-04-24
It's worth noting that XFS and grub don't play well together.

---

### Post by chucky chuckaluck on 2008-04-24
are there drawbacks to ext3, other than "it's not the fastest"?

---

### Post by mips on 2008-04-24
> **Simpatico said:**
> It's worth noting that XFS and grub don't play well together.

Thats nonsense. It used to be the case many moons ago but no longer so. XFS & grub work just fine together. If you don't believe me try it.

---

### Post by mips on 2008-04-24
> **chucky chuckaluck said:**
> well, i was hoping for a one file system answer (i should have known :rolleyes:). to be perfectly candid, i really haven't understood half of what you guys are saying. so, with that in mind, if i were to pick one file system for the whole mess, given that i'm pretty much of a minimalist end user, what would you all pick for me? 

btw, i do appreciate the in depth responses, even if they're currently over my head.

[http://linuxgazette.net/122/TWDT.html#piszcz](http://linuxgazette.net/122/TWDT.html#piszcz)
[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

I use XFS on all my partitions as it seems to be the best compromise out of the lot. I have never lost any data on a XFS partition even with power failures **BUT** I also have a 500GB external Ext3 backup drive for my data which one should have anyway.

Using Reiser for things lke /var etc will probably speed things up even more but I'm settling for one FS and that is XFS.

---

### Post by bonzodog on 2008-04-24
I use reiserFS across my entire system, and it's great. I once had a box power down in a sudden brown out with a few files open, and was thinking I might have corrupted the FS -- nope, it rebuilt it, and recovered the bad files.

For Arch, like the first poster says, ReiserFS is great. One of the big downsides of Ext3 is the FS check every 25 boots, whereas ReiserFS does not do that.

---

### Post by Rumor on 2008-04-24
> **chucky chuckaluck said:**
> are there drawbacks to ext3, other than "it's not the fastest"?

I use ext3 for my / and my /home. I have not noticed any drawbacks. Arch has run quite nicely for the last nine months or so since I built the system.

---

### Post by articpenguin on 2008-04-24
> **chucky chuckaluck said:**
> are there drawbacks to ext3, other than "it's not the fastest"?

yes 

1.static amount of inodes which means you can only have a limited amount of files.

2.slow on large deletions

---

### Post by chucky chuckaluck on 2008-04-24
what about compatibility issues with the various file systems? i saw some comment on one of the links mips provided (thanks, mips) that suggested that various tools were written with ext3 in mind. (i had no idea what he was talking about.)

---

### Post by articpenguin on 2008-04-24
> **chucky chuckaluck said:**
> what about compatibility issues with the various file systems? i saw some comment on one of the links mips provided (thanks, mips) that suggested that various tools were written with ext3 in mind. (i had no idea what he was talking about.)

one advantage with ext3 that it is backwards compatible with ext2 and foward compatable with ext4(ext4 still is in development.

ext3 is just ext2 with a journal.

ext4 has extents, and a lot of new features.

---

### Post by Simpatico on 2008-04-24
> **mips said:**
> Thats nonsense. It used to be the case many moons ago but no longer so. XFS & grub work just fine together. If you don't believe me try it.

I did when Zenwalk 2.8 was new, and had problems.  I expect that is the reason they still used lilo, in addition to their Slackware base.  That was only two years ago.

---

### Post by Pogeymanz on 2008-04-24
I don't want to hijack this thread, but I have some questions.

How do the filesystems perform with respect to fragmenting?

And which filesystems have journals, and are those considered "safer"?

Also, how big should one make /var if it has its own partition?

---

### Post by mips on 2008-04-24
> **chucky chuckaluck said:**
> what about compatibility issues with the various file systems? i saw some comment on one of the links mips provided (thanks, mips) that suggested that various tools were written with ext3 in mind. (i had no idea what he was talking about.)

I speak under correction but I think the situation has improved wrt tools for other filesystems. XFS for example is being included in FreeBSD 7 (read only at this stage I think).

---

### Post by articpenguin on 2008-04-24
> **EmosSuck777 said:**
> I don't want to hijack this thread, but I have some questions.

How do the filesystems perform with respect to fragmenting?

And which filesystems have journals, and are those considered "safer"?

Also, how big should one make /var if it has its own partition?

They all fragment. JFS fragments the most in my experience. Dont know about reiserfs or xfs. I think xfs fragments because it has a defragger. Ext3 seems to be the most resistant to fragmentation.

JFS XFS Reiserfs and ext3 are all journalled though reiserfs and xfs corrupt easy. 
[http://linuxmafia.com/faq/Filesystems/reiserfs.html](http://linuxmafia.com/faq/Filesystems/reiserfs.html)

ext3 is considered the most stable filesystem. The other 3 journalling filesystems are mixed with most people saying xfs and reiserfs corrupting easy. JFS Seems to be stable too with crashes IMO.

---

### Post by FredB on 2008-04-24
Forget reiserfs, it seems to be a dead end for now. Stay on ext3.

---

