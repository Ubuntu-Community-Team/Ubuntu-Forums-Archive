---
title: "How to format disk?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by pointyblue on 2007-07-12
Ubuntu 7.04 takes up all 250 GB of my harddisk. I need to make a dual boot disk with both win XP and Ubuntu.

Stupid Win XP will not install as long as Ubuntu is on the disk - so I need to format the disk and install XP first and then Ubuntu.

But how do I format the disk?

---

### Post by twiceasworn on 2007-07-12
If you stick in the Win xp disk it should have an option of formatting the disk (erasing everything) and installing windows.

Or you could look at Gparted (partitioning tool) that would let you resize the ubuntu partition to make room for the Win XP.

---

### Post by sugarland2k on 2007-07-12
Try to load the Ubuntu Live CD if you have one.  If your on a network, you might want to load Gparted or try Gparted Live.

Some good sites...
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

[http://www.linux.com/articles/53924](http://www.linux.com/articles/53924)

With Gparted, you can resize your Ubuntu (Linux) partition and make room for Windoze.   I have run Ubuntu in partitions as small as 30GB.  

Good luck - if you need assistance, let us know on this forum!

---

### Post by pointyblue on 2007-07-12
Unfortunately I can't just insert the win xp disk and let it do the work for me. It's a master disk created with an image of how the computer was when I bought it and having to deal with a disk with linux on it seems to be a little to complicated for it.

I called Packard Bell support and asked them for help but they didn't know what to do once they heard I've installed a linux system! The only advise they gave was that the master disk would not run unless I found a way to format the disk and start all over. And being unfamiliar with the mysterious ways of lunix they had no idea how to do just that.

Anyway, I'll try gparted, it sounds promising. Thanks!

---

### Post by the.phantom on 2007-07-12
maybe this is close?"

i have win98 and u

to do it i had to
do a "restore disk" to clean up all the windows junk,
once i got windows lean and mean i could change the size of it's partition and then i could install U ( size change with qtparted)
this is a fat32 windows but the way should be the same
fresh restore (after backing up personal data)of windows
partiton size change
then install U 

only hint is to defrag windows a few times first !

you might have to enable the xp format to repart?

---

### Post by Al3xK3aton on 2007-07-12
Why is a single linux install taking 250GB? Mine doesn't take that much. Is it possible that you have a virus or spyware?

---

### Post by Redache on 2007-07-12
I think he means that the partition is the whole disk.

Try resizing, it's doubtful the master image would really notice a different partition size, unless Packard Bell are really irritating.

---

### Post by davidjmayo on 2007-07-12
> **Al3xK3aton said:**
> Why is a single linux install taking 250GB? Mine doesn't take that much. Is it possible that you have a virus or spyware?

What?

Do you think OP might have chosen to use entire hard drive during the install?

---

### Post by lisati on 2007-07-12
> **twiceasworn said:**
> If you stick in the Win xp disk it should have an option of formatting the disk (erasing everything) and installing windows.

Or you could look at Gparted (partitioning tool) that would let you resize the ubuntu partition to make room for the Win XP.

It might be possible to use something like Gparted to make room for Windows & create a FATxx or NTFS partition - if you're lucky the recovery tools won't clobber the Ubuntu partions, or have an option not to resize.  From what I've read in other threads is that it might be necessary to re-install Grub afterwards.

---

