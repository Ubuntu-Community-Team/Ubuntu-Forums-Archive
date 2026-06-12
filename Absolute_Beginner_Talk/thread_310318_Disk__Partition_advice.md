---
title: "Disk / Partition advice"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Cave Dweller on 2006-12-01
Greetings all.

I was hoping to get a little advice, please.  Here's a quick "story so far".

I was running a dual boot setup, with XP on a 40 gb drive and Ubuntu on a 20 gb slave.  One day something nasty happened to my XP, and rather than re-install, I've been using Ubuntu for everything, I'm pretty lazy.  I've finally finished dragging everything I could of what I wanted from the 40 gb drive onto the 20, which is now pretty much full, and I'm wanting that 40 gb back.

Is there a decent hard disk testing utility?  I'd like to check the drive, first, if I can.

Can I somehow move Ubuntu onto the larger disk?  Or would it be easier to re-install.  I'm thinking the bigger drive is probably faster, is there maybe a small benchmark tool?

Also, I have been using the default partition scheme on the 20 gb drive.  Just the one large partition and swap.  But since I will now have two drives, I was wondering what my options were.  Can I stick the two together so that the filesystem treats both as the one partition?  Or should I go for multiple partitions?

I'm afraid I'm still learning my way around the hierarchy, so I'd like to keep things fairly simple, but a friend said I should have these partitions, and then rattled off a list of about six or eight.  So I dropped in for some help.

I know this is kind of off topic, but I'm curious.  I think my friend uses free bsd.  Is this really so different to linux?  I get the feeling that he doesn't think all that much of linux.  He didn't say it in so many words, but the tone of the conversation was along the lines of:  At least it's not windows, but when you're ready for a real OS let me know.

I'm sorry if this post rambles a bit.  Thanks for taking the time to read it, and maybe posting your thoughts.

---

### Post by Shay Stephens on 2006-12-01
I would turn the 40gb into a data drive.  Keep ubuntu on the 20gb, and move/save all your data on the 40gb.  That way, if you hose the ubuntu drive, your data is left safe.

---

### Post by RMorris78 on 2006-12-01
My favorite programs for testing hard drives are [Hitachi DFT]("http://www.hitachigst.com/hdd/support/download.htm") or [Seatools]("http://www.seagate.com/support/seatools/")

This is helpful for the difference between BSD and Linux

[http://www.freebsd.org/doc/en_US.ISO8859-1/articles/explaining-bsd/comparing-bsd-and-linux.html](http://www.freebsd.org/doc/en_US.ISO8859-1/articles/explaining-bsd/comparing-bsd-and-linux.html)

---

### Post by CatKiller on 2006-12-01
> **Cave Dweller said:**
> Is there a decent hard disk testing utility?  I'd like to check the drive, first, if I can.

The manufacturers of the hard drive normally include a program you can put on a boot floppy to test the disk.

> Can I somehow move Ubuntu onto the larger disk?  Or would it be easier to re-install.

You can. The easiest way would probably be to use **dd** to do a bit-by-bit copy of your smaller drive to your larger - MBR and all - then use **gparted** to expand the partition to take up the whole of the larger drive. Then swap the drives around. You'll want to do this from the install disk rather than from your normal Linux environment, and the dd part **will** take a long time. If you've not done anything to your existing install, it might be quicker to re-install.

> Can I stick the two together so that the filesystem treats both as the one partition?  Or should I go for multiple partitions?

Really, it's going to treat them much the same anyway. When you mount the other partition, it will be put at a point in the filesystem. Whether this is at [/home]("http://www.psychocats.net/ubuntu/separatehome") or as /media/data or whatever is completely up to you. But you won't have drive letters or anything to worry about.

---

### Post by Cave Dweller on 2006-12-02
Thanks everyone.  I really enjoy these fora, but everything is still so new, that I'm easily distracted.

Seatools didn't find any errors on my drive, so far everything looks good.

Shay, I found a couple of nice threads that will walk me through doing that.  I think it's a good idea.

I had a quick look at the dd --info, last night.  I'm about to take a longer look here.

I'm wondering, if I fresh install onto the empty drive, will I run into file ownership problems trying to access stuff stored on my current file system?

---

### Post by CatKiller on 2006-12-03
> **Cave Dweller said:**
> I'm wondering, if I fresh install onto the empty drive, will I run into file ownership problems trying to access stuff stored on my current file system?

Please don't take this as definitive, but I believe that user access is defined by the user ID number. For both Ubuntu installs, the users will start at 1000 and be incremented by 1 for each new user. So if you create new users in the same order on the second install as on the first, then they will effectively be the same user on the second install as on the first.

Failing that, you can always temporarily assume root privileges with **sudo** long enough to sort out any permissions problems you might be having.

---

### Post by sardion on 2006-12-03
Catkiller is correct.  Ownership is by user id (UID) and group id (GID).  As long as the original ubuntu install was just one user, the one created during setup (which is true for 99% of desktop ubuntu systems) then a clean install will not give you any ownership issues.

---

### Post by Cave Dweller on 2006-12-04
Thankyou :)

---

### Post by bodhi.zazen on 2006-12-04
gparted will copy partitions. Boot gparted, delete your ntfs partition, copy the ubuntu partition to the 40 Gb drive, resize if needed....


Modify /boot/grub/menu.lst to point to the first HD.

Post if there is a step you do not understand....

[gparted live cd](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

