---
title: "Best hard drive setup"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by IntoTheLight on 2006-12-31
Just checked out the Live CD 6.06 LTS that my sup passed off to me.  Freakin' Awesome!  Never dealt with Linux, but I am definitely ready to give it a go.  I have been doing a lot of reading around the web, and even picked up a book called "Ubuntu Hacks".  

I have seen a lot of different things about the setup of the hard drive, but it's a little confusing, so I'm wondering if someone can help me out.  I have a 250G HD that will stay with that other system for now, and a 120G HD that can be used exclusively for Ubuntu.  I also have an external 300GB HD (FAT32) that I can use to share between the 2 OSs (until I do away with the other one).  

root, home, user..., I have no clue how to divide all of these, and how much space each needs.  Also, do each of these get a partition to themselves? Oh, swap, I've got 2MB Ram.  I want to not have to worry about moving things around for a while, and would prefer to have everything set for ease of use, and ease of repair.

Thanks!

---

### Post by &#12465;&#12452;&#12488; on 2006-12-31
```
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             6.0G  4.4G  1.7G  74% /
/dev/sda3              48G   19G   30G  39% /home
/dev/sdb1             233G   42G  192G  18% /media/gnawty
```

I have a 60 GB HDD in my laptop; *sda*. When partitioning it, I split the disk up in three parts; / (root), swap and /home. root got 6 GiB, I made the swap partition the same size as my amount of RAM, and put all the remains into home. You generally won't be needing so much space for your root partition, as you can see above I'm only using 4.4 GiB at the time writing, and I've used this install for a long time. I think it might be enough to put 256 MiB for swap, because the system seldom uses it as all now that we've got so much RAM. But if you really want to be 105% certain you'll never use all the swap, do feel free to add more!

*sdb* is my external hard drive, and you could mount your huge FAT32 disk the same way.

---

### Post by rfruth on 2006-12-31
So you have 3 physical hard drives, can you unplug all but Ubuntu drive & let Ubuntu do its install thing otherwise need to know where Ubuntu goes (e.g /dev/sda1)

---

### Post by Bartender on 2006-12-31
If your hard drives are PATA, they'll be identified as hda and hdb.  Then partitions on first disk will be hda1, hda2, etc., and partitions on second disk will be hdb1, hdb2, etc..

If SATA sda and sdb. 

I think what you'd want to do is toss the LiveCD in, and when you get to the partitioning part choose "manual partition".  Make sure you install Ubuntu to hdb.  Just mount / and swap to that drive.  Ubuntu will only make 2 partitions, one for the main install and one for swap.  At the very end of the partitioning process, just before it's ready to install, there will be a summary page.  There's a little box in the middle of the page.  Easy to miss.  Make sure that GRUB will install to hd0.  That's the very front of the first HDD.  GRUB should tweak MBR so that you'll get a menu when starting that gives you the option of which OS to boot.  That's for a standard dual boot.  If you want to make a separate home partition it's not hard, but what I describe is the simplest.

I've not gone thru the steps with 2 distinct drives both hooked up at once so I hope someone else verifies or refutes. 

Actually, what I'd do is download the GParted Live CD, burn to a CD, and use that to format the second drive, set up the partitions, etc.  Then I'd go ahead with the UbuntuCD.

EDIT: what rfruth describes is the safest.  That way you know you're not going to affect the Windows drive.  There have been several posts on this sort of thing lately.

---

### Post by jkrtest on 2006-12-31
This pretty much the info I've been looking for, too.
One further question: does it matter which one is a primary and which are extended partions?

Cheers!
==k

---

### Post by Bartender on 2006-12-31
Windows won't start from within an extended partition.  Linux will.  You can make 3 primary partitions with a partitioning tool like GPartedLiveCD.  The rest will have to be logical partitions within the extended partition "box".

---

### Post by jkrtest on 2006-12-31
Ah, OK.
So this is what I am planning:
win2000	20GB
Docs	5GB
Pics	50GB
Music	20GB
Movs	80GB
/home	10GB
/	6GB
/swap	1GB

total	192GB

It will be the only drive (~200GB).
I'd like to reserve the first 20GB in case I have to install Windows. That'll be my promary partition, probably already formatted in NTFS. Maybe I won't bother.

Is there any advantage of making any of the other partions primary or can all but the first one be logical?

==k

---

### Post by IntoTheLight on 2006-12-31
Ok, but here's the thing...

I have no reservations about performing the install, or partitioning the drives.  What I am asking is...

If you had a 120GB HD that was for Ubuntu only, with a 250GB HD that would not be touched, and a 300GB HD for sharing files between the 2 OSes, how would you set up the 120GB HD?  What is easiest now is of little concern.  I want what will be easiest when I want to upgrade, I have to re-format, or whatever.  I plan to add a ton of different apps, and I am pretty much thinking that the Gates abortion will be an as-needed thing until I get this OS figured out.


What goes into root, home and all these other sections?  What's the best way to divide the drive?

---

### Post by jkrtest on 2006-12-31
I read this veryhelpful site:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

At the bottom of the page there's some reasoning for having the /home partition separate.

I also read that if one has 1GB of RAM or more, a separate /swap partition is not necessary.

HTH,
==k

---

### Post by handy on 2007-01-01
You may find this thread useful:

[http://ubuntuforums.org/showthread.php?p=1952923#post1952923](http://ubuntuforums.org/showthread.php?p=1952923#post1952923)

Post# 79. is how I do it! :KS

---

