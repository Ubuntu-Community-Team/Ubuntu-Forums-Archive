---
title: "disk defragmentation tool in Ubuntu"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-21
is there a disk defrag tool included in Ubuntu 7.10?  if not, what would be the best tool to use for this task?  thanks.

---

### Post by jeffus_il on 2008-01-21
It is not necessary to defrag Linux file systems.

---

### Post by oodledoodle on 2008-01-21
as above, the filesystems used in linux do a good job of keeping themselves in check. so go and have a beer instead of having to worry about defragging ever again.

---

### Post by PeterJS on 2008-01-21
There is, it's called fsck, and it runs automatically every 26 boots.

---

### Post by duruttye on 2008-01-21
I think defragmenting is only for NTFS file system, so you don't have to be worried to defragment ever!

Why do you want to do that anyway?

---

### Post by Jonne on 2008-01-21
fsck doesn't defragment, it checks the filesystem for corruption and such. Ext3 and such don't need to be defragmented, as fragmentation happens less frequently due to the way that files are written to disk.

---

### Post by PeterJS on 2008-01-21
> **Jonne said:**
> fsck doesn't defragment, it checks the filesystem for corruption and such. Ext3 and such don't need to be defragmented, as fragmentation happens less frequently due to the way that files are written to disk.

Really? hmm learn something new everyday. I through shuffling things around on disk to reduce fragmentation was one of the things it did, hence why it can't be done on a live file system.

---

### Post by LeAstrale on 2008-01-21
the reason that you need to defrag windows from time to time is because you have the pagefile on the same partition as any other data.. that means that data come and go very frequently which leads to files being cut in many small places to fill the "holes" in your disc layout.

---

### Post by toastysquirrel on 2008-01-21
I have a semi-related question.  I'm dual-booting between XP and Ubuntu so my main data drive is NTFS formatted.  Is there a utility that will allow me/us to defrag foreign-formatted partitions?

---

### Post by LeAstrale on 2008-01-21
> **toastysquirrel said:**
> I have a semi-related question.  I'm dual-booting between XP and Ubuntu so my main data drive is NTFS formatted.  Is there a utility that will allow me/us to defrag foreign-formatted partitions?
that im not able to answer you. But why do you want to defrag from ubuntu if you have windows on the computer too ?

---

### Post by toastysquirrel on 2008-01-21
> **astral-1 said:**
> that im not able to answer you. But why do you want to defrag from ubuntu if you have windows on the computer too ?
I'm looking to minimize my exposure to Windows as much as possible; kind of like radiation you know.  I haven't booted into XP in two days, I'd like to keep that trend going so I'm on the look out for as much Windows functionality as I can possibly get. ;)

---

### Post by brennydoogles on 2008-01-21
> **toastysquirrel said:**
> I have a semi-related question.  I'm dual-booting between XP and Ubuntu so my main data drive is NTFS formatted.  Is there a utility that will allow me/us to defrag foreign-formatted partitions?

+1 to this question. I have an external drive formatted to NTFS so I can share huge files with other people, most of whom use windows. As I don' t have windows installed on my computer, how could I defrag this drive?

---

### Post by Jonne on 2008-01-21
> **toastysquirrel said:**
> I'm looking to minimize my exposure to Windows as much as possible; kind of like radiation you know.  I haven't booted into XP in two days, I'd like to keep that trend going so I'm on the look out for as much Windows functionality as I can possibly get. ;)
ntfsdefrag, part of the ntfsprogs package should be able to do it. Although I've never used it, and you shouldn't blame me if it turns out that there's a bug that wipes all your data ;) .

edit: i spoke too soon: [http://www.linux-ntfs.org/doku.php?id=ntfsdefrag](http://www.linux-ntfs.org/doku.php?id=ntfsdefrag)

Apparently you'll need to write it first before you'll get to use it ;).

---

### Post by Matt26 on 2008-01-21
so is there a defrag utility that comes with Ubuntu?  in case i missed it, i don't think that this question was answered.  if there is not could someone recommend a good one? thanks.

---

### Post by Jonne on 2008-01-21
No there isn't, as you don't need it.

Actually, NTFS also does a decent job in not fragmenting itself, so defragging isn't really necessary for that either (unless you deal with lots of big, growing files, like when editing video).

---

### Post by apostate on 2008-01-21
Matt, buddy, that's what the answer is... No, because you don't need one. The EXT3 filesystem does not fragment, thus, a defrag utility is pointless. It's like a toilet-seat cover for a urinal. Un-useful.

Enjoy a beer instead of defragging.

---

### Post by toastysquirrel on 2008-01-21
> **apostate said:**
> Enjoy a beer instead of defragging.
Best suggestion I've heard all day.

---

### Post by p_quarles on 2008-01-21
There is one, and it's called "defrag." You can install it by searching the repositories.

HOWEVER: it's very old, and I understand that's it a bit undermaintained. I would strongly recommend not using it. 

Journaling filesystems experience some fragmentation, but under most circumstances, it will never amount to anything noticeable, even after running for years. 

For special circumstances where fragmentation does occur, there are tools that you can get.

---

### Post by jeffus_il on 2008-01-22
If someone feels an intense drive to defrag, maybe originating somewhere in the early childhood years, resulting from a negligent father who couldn't bring himself to defrag, simply do this, you need no extra software (compulsive installers are always looking for another piece of software to install, probably a result of strong marketing):[LIST]
[*]create a new temporary partition big enough to hold the content of the drive to be defragged.
[*]copy the whole filesystem to the new partition using a recursive copy which keeps permissions on files. ```
cp -rpv /dir/source /dir/temp
``` r for recursive, p for preserve and v to keep your eyes busy while its alll happening.
[*]delete the original filesystem or create a new one on the same partition.
[*]copy the filesystem back using the same command reversed.
[*]the filesystem is now 100% defragged.[/LIST]Don't take this personally, some of my best friends have been known to defrag, I have also done it a few times, that's how I know how to do it, but I wouldn't admit it in public.
There's a mistake in the cp command, it needs a "*" somewhere.

---

### Post by misfitpierce on 2008-01-22
The disks as said in Linux maintain themselves. Every 24-26 boots it will check the disk at bootup to ensure everything is proper as it should be then it will continue boot as normal. Another great linux innovation.

---

### Post by articpenguin on 2008-02-01
all files over 128MB will fragment on ext3. Its the way ext3 is designed

---

### Post by Herman on 2008-02-03
Here are a couple of nice informative links that some of us might find interesting, 

[CENTER][OneAndOneIs2 - Why doesn't Linux need defragmenting?]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")
                        
                        [ITworld.com - Fragmentation and Unix file systems]("http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html")

[LEFT]Regards, Herman :)
[/LEFT]
[/CENTER]

---

### Post by geo909 on 2008-02-03
> But why do you want to defrag from ubuntu if you have windows on the computer too ?

 What about this scenario: An external disk in NTFS..
Such a disk for *storage* purposes, doesn't it need defragmentation?
(Not a rhetorical question, I really don't know)

EDIT: Please Ignore this post, as it has already been answered before in this thread. I kind of missed the next pages!! Sorry for the spam...

---

### Post by chewit on 2008-02-03
I heard that ext3 does a mini defrag ever 25 to 30mins, not sure how true this is

---

### Post by insane_alien on 2008-02-03
ext3 will become less fragmented the more you use the filesystem. if yours is a busy filesystem where files are getting copied/deleted/created at quite a rate then it is probably that you'll have a less fragmented system than someone who doesn't do a lot of that. 

that said, ext3 will still fragment but at a much slower rate than ntfs or FAT32 and only if you use more than 60% of the filesystem. or if you do a lot of torrenting with no full allocation.

in a year perhaps we will see the inclusion of ext4 into ubuntu. this is the next generation of the ext filesystem. while it will have an increased capacity to stay very defragmented it will also have an online defragmenter. in general it will be better all round.

i have a 2 year old ext3 partition on my system. its been heavily used and is about 75% full just now. fsck tells me the fragmentation is 0.12% pretty damn clean if you ask me. then again my torrent partition is at 17% fragmentation because when it startedi did not know to use full allocation. but it is getting better and i have never needed to defragment it. it used to be up at 26%.

---

### Post by Matt26 on 2008-02-05
should there be any consideration given to fragmentation in the case of a PC that is powered on 24/7?  my machine is always on, so i don't know if this situation would mean any difference in how the filesystem on an ext3 volume fragments.

---

### Post by LowSky on 2008-02-05
> **Jonne said:**
> Actually, NTFS also does a decent job in not fragmenting itself, so defragging isn't really necessary for that either (unless you deal with lots of big, growing files, like when editing video).

I defrag my NTFS every 3-4 months, as it is always fragmented more than 10% by that time. The bigger the hard drive the more fragmented your files like to become. And for some reason Windows like to throw data on the middle of a partition, especially inmovable data, which becomes annoying when you want to shrink or manage a partition.

---

### Post by articpenguin on 2008-02-06
Overall all linux filesystems will fragment but not as much as fat or ntfs.

JFS and reiserfs fragment the most.
ext2/3 wont fragment as much but will fragment on a file over 128MB.
XFS fragments the least as it has various techniques such as delayed allocation,Extents and a B+ tree for indexing free space.

JFS also uses extents as well as NTFS and they both fragment, although JFS fragments less

---

### Post by philinux on 2008-02-06
fsck will run every "n" boots dependant upon the size of the file system. In my case this was 36 boots. You can check this interval by using

sudo tune2fs -l /dev/sdaX

I've changed mine to 50 boots by using

sudo tune2fs -c 50 /dev/sda1

On fragmentation read this.

[http://felipecruz.com/blog_linux-defrag-fix-fragmentation.php](http://felipecruz.com/blog_linux-defrag-fix-fragmentation.php)

---

### Post by bsmith1051 on 2008-02-07
It really bothers me when people insist that "Linux", or more properly, EXT3, doesn't need defragmenting.  Take it from an old-timer like me, EVERY OS has made this claim and its simply not true.  Instead, it's all a matter of relative need-to-defrag.  I understand that EXT3 is more resistant to fragmentation than NTFS, but if you ever get anywhere near 'full' on the partition you'll get some really really badly fragmented files.  That's the other misinformation -- the fsck 'fragmentation' level.  It doesn't matter if 99.5% of the files are unfragmented if the files you actually use regularly (the other 0.5%) are massively fragmented.

That said, I haven't tried to implement the old 'defrag' tool mentioned earlier.  I think you have to dismount your partition?  And, frankly, I reinstall from scratch often enough (every 6-12 months) that I don't worry about fragmentation.

Ultimately, I'm waiting for EXT4 (which includes 'online' defrag) or whatever else people adopt as the new standard.

---

### Post by Herman on 2008-02-07
:) I just make sure my partition and file system is large enough to comfortably house all my files. If it gets much more than around 80% full I either resize the partition or delete some files.

Regards, Herman :)

---

