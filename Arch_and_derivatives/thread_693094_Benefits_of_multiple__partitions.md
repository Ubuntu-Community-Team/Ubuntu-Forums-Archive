---
title: "Benefits of multiple  partitions"
date: 2008-02-10
forum: Arch and derivatives
---

### Post by PurposeOfReason on 2008-02-10
I was wondering if having a seperate partition for / /var and /home would have any benefits and if so, about what size would be best for /var? Also, are there any other mountpoints I should put seperate? I've always just used / for everything.

Unrelated: Has gparted been fixed to where it can resize a vista partition properly?

---

### Post by em3raldxiii on 2008-02-10
Hi P.o.R.,

The answer is going to depend a little bit on what you are using your system for.  For example, if you are running a LAMP (Linux Apache mySQL PHP) server on your computer, then putting your /var directory onto it's own partition is a great idea.  It allows you (if need be) to re-install or completely change your operating system without losing the contents of /var (which usually includes your entire website and database).

/home should always be (in my opinion) on it's own partition.  This allows you to much more easily save your data if you do something bad to your root, or if you plan to do a complete re-install.  Plus, it's handy for networking situations where you want to share the partition over the network.

As for size, it will depend on the content.  /var can be smaller if you are not running a server, and /home is usually quite large for downloaded multimedia content.

Alternatively, you could make separate partitions for individual media types.  I have, for example, created separate partitions for /media/music and /media/movies.  My music collection is around 8GB (I know, large, but not as large as some people) and my movies collection is >60GB.  I back up all of my movies because I have kids who are very rough on DVDs and VHS tapes degrade a lot over time; and with music, I generally make lossless backups of my CD collection (FLAC format is your best friend).

An added benefit (this is based on only what others have told me, I have no concrete proof), is that access is more efficient.  Since the partitions are "pie-piece shaped chunks" of your drive, it's actually faster for your drive to access data across partitions than it would be if it was all one large partition.

Hope that helps!

---

### Post by PurposeOfReason on 2008-02-11
This is just going to be a standard laptop computer not doing anything fancy. I was thinking about the following, with swap thrown in there somewhere. It's a 120GB HDD so if my numbers are off, or something should be bigger, feel free to adjust them to your whim. :)

/vista 23GB
/     8gb
/home    15gb
/usr    10gb
/var     8gb
/storage    56gb (that's where I keep all my music and documents)

Someone in the arch forums recommended using a /usr, not too sure why. Amongst this, are there ary certain file system types that would be better for each partition?

---

### Post by Tenken on 2008-02-11
I think one reason /usr is suggested is because most AUR packages are configured to build in /usr/local by default.

---

### Post by em3raldxiii on 2008-02-11
I'm not entirely sold on the necessity of having /usr on it's own partition.  I'd be inclined to just leave that one in / ... then split the space you had for /usr between / and /home ... so for me, (and this is just what *I* would do with your drive ....

/vista 30GB <--- Space-Hog ... needs room to breathe.
/ 10gb <--- a bit of extra room for *whatever*.
/home    16gb <--- This one is flexible, obviously
/var     8gb <--- could be a bit smaller if you are not running any servers or anything
/swap 2GB <--- my rule of thumb is double your RAM, so resize accordingly.
/media/storage *the rest* (120GB drives are not always reported as exactly 120GB for relatively obvious reasons)

I moved the /storage into /media/storage so that it is in the same place as CDRoms and stuff.

As far as file systems are concerned, I generally default with EXT3 for all my linux stuff; For XP I would go with NTFS, and I think Vista has it's own newfangled file system.

Anyway, I hope that helps.  Keep us posted :D

---

### Post by PurposeOfReason on 2008-02-11
Well after talking it over and much reading of wikis, it's looking to be like this and in this order from left to right if you were looking at gparted:

/vista recovery 4GB (I believe)
/vista 25GB  NTFS
/swap 2GB  SWAP
/ 10gb  EXT3 (maybe REISERFS, if there really isn't a downfall. It's supposed to be faster with smaller files)
/home 14GB EXT3
/var 8GB REISERFS
/media/storage  (shatever I have left) EXT3

I'll set it up in gparted before as fdisk and cfdisk aren't as convienent and I don't have a live gparted disk for nothing. The part starts on Wednesday, Tuesday if I'm lucky. I give it five hours (I hate my connection )from computer ariving to having everything up and going in xfce. :)

Just curious, is there any real benefit to putting storage in /media besides orginization and, still, is the vista risizing fixed yet with gparted yet? If not, I should be able to use the recovery partition to fix that one file, right?

Finally, as I've never had to use an extended partition before, I should just put everything from swap on into the extended partition?

---

### Post by Gigamo on 2008-02-11
I would put / on a primary partition, and swap + everything after / on logical ones.

---

### Post by PurposeOfReason on 2008-02-12
> **Gigamo said:**
> I would put / on a primary partition, and swap + everything after / on logical ones.
Any particular reason for doing this?

---

### Post by PurposeOfReason on 2008-02-13
Well I just started partitioning, time me. ;) Might take longer because I think I just broke vista, it said it was moving it . . .

---

### Post by em3raldxiii on 2008-02-13
Hmm, one common issue with partitioning after VISTA is where Vista puts it's boot record ... So when you put Ubuntu on it, you might lose the ability to boot into your Vista.  There is an easy fix for it out there .... but I don't remember it off the top of my head.  Do a search for repartitioning with Vista/Ubuntu and you'll probably find a relatively simple fix.

As far as types of partitions ... well, I have a simple habit of always putting everything on primary partitions.  To be honest, I am not really sure which way is better.  At this point, I could be convinced either way.

I'm at work, so I probably won't have a chance to help you later.  However, if you can get *something* working, then you should be able to get realtime help on the IRC channel.  .... I can't remember the server off the top of my head, but I believe it's on freenet.net; the channel is #ubuntu and if that's too busy, try #ubuntu-offtopic but be ready for someone to growl at you and send you back to #ubuntu.

---

### Post by PurposeOfReason on 2008-02-13
Lucked out, Vista lived (we all know how hard Microsof is to kill ;)) and arch is installed (just have to do all the real work) but I'm going to work on this dead pixel it came with before I go any further. I hate how one pixel isn't enough to warrent anything. You need like ten. :(

---

### Post by em3raldxiii on 2008-02-13
Wow, that's frustrating.  Luckily the folx I usually buy my computer hardware from have a "zero dead pixel" insurance policy.  It costs an extra coupla bucks, but if it has any dead pixels you can send it back and get a replacement.

I'm glad all your mad partitioning didn't kill your Vista.  Not that I am condoning wasting hard drive space on it ... just that I'm glad you didn't run into any serious hangups.  Now ... we just have to work on you to convert your entire Vista partition to EXT3 .... :twisted:.

PS ... I visited your deviantart page ... nice stuff.  I like those ubuntu-ish curve images.  I never thought of setting up my own deviantart page, but you just inspired me :D  Cheers!

---

### Post by PurposeOfReason on 2008-02-13
Thanks for that, everything is all setup now. I keep the vista around because of college and that since this model has two graphic cards and can only switch on a reboot, I might as well turn to the nice nvidia, reboot, and game without having to worry about wine.

The pixel left for a while, then came back. I'm going to run one of those flashing color things all night to see if it gets it. If not, I have a light theme. :)

---

### Post by em3raldxiii on 2008-02-14
Yeah, gaming is still a little ways away from serious mainstream on Linux.  It's coming though ... I can feel it :D

---

### Post by perspectoff on 2008-02-20
One advantage of separate partitions for the operating system and the data files is the possibility of using LVM for the data partition. That way, if you reach your capacity on the data partition, you can increase storage using LVM.

A disadvantage of using multiple partitions if you don't use LVM is that you will eventually fill up the partition, and it is harder to move and consolidate files over multiple partitions (if not using LVM).

---

### Post by regbsn on 2008-03-02
What is LVM?

And...How do I use it?

---

### Post by mips on 2008-03-03
> **regbsn said:**
> What is LVM?

And...How do I use it?

[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)
[http://wiki.archlinux.org/index.php/LVM2](http://wiki.archlinux.org/index.php/LVM2)
[http://wiki.archlinux.org/index.php/Lvm](http://wiki.archlinux.org/index.php/Lvm)
[http://bbs.archlinux.org/viewtopic.php?pid=223327](http://bbs.archlinux.org/viewtopic.php?pid=223327)

---

### Post by frankos44 on 2008-03-03
Remove Vista.. yuk!

I see no benefit of using separate partitions on a desktop PC on a single hard drive. 

1. There will be no speed improvement when using a single hard-drive. In fact the heads on the hard-drive will have to seek further and make it slower if anything. 

2. The structure of Linux computers if very efficient and does not suffer from fragmentation like MS machines. On windows multiple partitions does help the 'Lost space' and 'Fragmentation' issues. 

3. I would not even consider re-loading an OS without backing up first. USB backup drives are so cheap and quick and you should backup anyway.

4. Backing up is so simple using tar, you can include or exclude folders of your choice.

You will however benefit from partitions if you have more than one hard-drive. The heads on one drive can seek independent from the other.

Your live web-server in my opinion should be a separate machine to prevent service interruption.

---

### Post by PurposeOfReason on 2008-03-03
> **frankos44 said:**
> Remove Vista.. yuk!

I see no benefit of using separate partitions on a desktop PC on a single hard drive. 

1. There will be no speed improvement when using a single hard-drive. In fact the heads on the hard-drive will have to seek further and make it slower if anything. 

2. The structure of Linux computers if very efficient and does not suffer from fragmentation like MS machines. On windows multiple partitions does help the 'Lost space' and 'Fragmentation' issues. 

3. I would not even consider re-loading an OS without backing up first. USB backup drives are so cheap and quick and you should backup anyway.

4. Backing up is so simple using tar, you can include or exclude folders of your choice.

You will however benefit from partitions if you have more than one hard-drive. The heads on one drive can seek independent from the other.

Your live web-server in my opinion should be a separate machine to prevent service interruption.
I'd just like to say a few comments to this. Vista, in all it's flaws, came with the computer meaning I paid for it, I won't waste my money. Some of us are also in school and the whole world doesn't use open source meaning not everything works.

There is also a significant boost in pacman performance than before (I timed it and syncing takes a good 3 seconds less) when I have /var on it's own partition.

---

### Post by frankos44 on 2008-03-03
> **PurposeOfReason said:**
> I'd just like to say a few comments to this. Vista, in all it's flaws, came with the computer meaning I paid for it, I won't waste my money. Some of us are also in school and the whole world doesn't use open source meaning not everything works.

There is also a significant boost in pacman performance than before (I timed it and syncing takes a good 3 seconds less) when I have /var on it's own partition.

Thanks, I am always interested in a different view.

I am surprised at the increase in performance all the same. I was looking at it from the hardware perspective i.e.  there is only one mechanism inside the drive moving the heads.

If you are correct and I have no reason to doubt you, perhaps the kernel gives different priorities for cacheing on individual partitions. This could account for the increase in speed with pacman but perhaps at the expense of something else.

I would love to know more about this if anyone wants to join in.

---

### Post by K.Mandla on 2008-03-03
I generally use a four-partition split, with no real reason aside from the fact that smaller partitions mount faster (and ext2 mounts faster than any other file system, supposedly, so all mine are ext2 with noatime). /boot is only 96Mb, / is 2048Mb, swap is 256MB and the rest (whatever it is) is /home. It works for me. :???:

---

### Post by Misbah on 2008-03-10
i like your partition set up.

I also put /, /home, /var, and swap on separate partitions.

some people suggest putting /usr and /tmp on seperate partitions, I do with arch, but not ubuntu because I don't think /usr and /tmp are used much when I look at my history and size using disk analyzer.

However, might I suggest putting /boot on a seperate ext2 partition as well?

---

