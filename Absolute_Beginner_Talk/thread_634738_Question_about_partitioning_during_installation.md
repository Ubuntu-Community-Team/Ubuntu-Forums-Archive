---
title: "Question about partitioning during installation"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Methuselah on 2007-12-08
First, my current setup:

HD1 with windows XP.
HD2 with a windows XP data partition and a FreeBSD boot partition.
Current boot manager is the Freebsd boot manager.

I want Ubuntu to use the FreeBSD partition.
I'm not sure what the partition dialog is saying though.
If I delete the FreeBSD partition (the only not identified as ntfs) and create and etx3 partition there, is that sufficient? 

Or, do I have to manually create two partitions with mount points "/" and "swap" respectively?. This is a little different from the FreeBSD installer where you can select free space and let it automatically split into the various filesystems. Maybe it's the terminology that has me a bit confused.

I'm a bit nervous to continue since my main files are on the windows partitions and I'm not backing anything up! (I have nowhere to put 100s of GB of data)

Thanks for any help!

---

### Post by Danikar on 2007-12-08
Delete the non NTFS one on your second hard drive and that piece will become unpartitioned.  It shouldn't touch your NTFS partition.

I would turn the unpartitioned space into 2 parts, one swap and one /.

Back up you stuff before doing so.

---

### Post by rsambuca on 2007-12-08
Do you realize that the hard drive failure rate is upwards of 8% per year?  I am always puzzled when I see people say they don't back-up their sensitive data.

---

### Post by Methuselah on 2007-12-08
Thanks for the info.
I had already used gparted to create the space for the FreeBSD partition from a large windows partition.
I figured out about deleting the FreeBSD partition in the ubuntu installation dialog.

I'm just a bit unsure about what the interface expects after that.

Do I need to select less than the total free space and have one "mountpoint" called "/" with the remainder having mountpoint "swap" (or is it "/swap")?

This is just a test installation so If I can get away without spliiting that would be fine. In that case, would I just set mountpoint="/" for that single partition?

---

### Post by Methuselah on 2007-12-08
> 
Do you realize that the hard drive failure rate is upwards of 8% per year? I am always puzzled when I see people say they don't back-up their sensitive data. 


Yeah, I've never backed up.
Hard for me to look at another hard drive full of duplicate data.

Fortunately, I haven't lost anything due to a crash yet.
I plan to set up a new system with large mirrored drives though.
It's dangerous to flirt with disaster for too long.

---

### Post by rsambuca on 2007-12-08
You are definitely treading on thin ice!  Good luck! 

As far as the installation goes, you can either:

1.  Partition manually during the installation process, creating space for root and swap, or
2.  You can Partition beforehand and install into the existing partitions.

Either work fine.

Personally I would go buy some DVD's to backup to first!

---

### Post by Methuselah on 2007-12-08
> **rsambuca said:**
> You are definitely treading on thin ice!  Good luck! 

As far as the installation goes, you can either:

1.  Partition manually during the installation process, creating space for root and swap, or
2.  You can Partition beforehand and install into the existing partitions.

Either work fine.

Personally I would go buy some DVD's to backup to first!

You see, I don't quite get this.
The options for "guided installation" all force me to use the whole disk.

However, when I choose manual (the only apparent way not to use the whole disk) I seem to be forced to do all the subpartitioning of the free space myself. This is the specific step that I need help on. 

If I just create an ext3 partition in the free space (deleted FreeBSD partition) and don't worry about setting mountpoint in the dialog will the installer divvy up the space for me (into root, swap etc)? If not, what's the minimum I need to do here?

Thanks!

BTW, I shudder to think of copying hundreds of GB onto DVDs...lol!
My current HDDs are not every old and the oldest one (5+ years) in a computer that I seldom use for serious work is still chugging along. I have one 10 years old with Windows 98  (backed up on the newer ones) that nontheless still works. Is this unusual?

---

### Post by rsambuca on 2007-12-08
I would use "Manual" partitioning.  You will need to create two partitions, one ext3 and one swap.  You will have to direct the '/' to the ext3 partition and the swap should fine the swap partition.

As far as the drive failures, when Google did a very in depth analysis of drive failures, the failure rate was a bit higher in the first year, and then leveled off around 8% every year for about 5 years, and then started to creep up.  Basically, after just 3 years, 25% of drives will have failed.  Surprisingly, temperatures and other factors had very little influence on failure rates.  I too have never had a drive fail, but I backup all of my photos and stuff routinely.  I do know a few people who have lost years' worth of personal photos and such, though.  Pretty sad.

---

### Post by Methuselah on 2007-12-08
> **rsambuca said:**
> I would use "Manual" partitioning.  You will need to create two partitions, one ext3 and one swap.  You will have to direct the '/' to the ext3 partition and the swap should fine the swap partition.



Thanks a lot for your great help.
One quick clarification: do you mean, the swap should 'find' the swap partition without me doing anything?

Also, will it automatically install a boot manager?
I already have the BSD boot manager but I'm not yet sure sure if it will automatically detect Ubuntu.

Boy, this forum sure does move fast.
I could barely find my thread after returning.

---

### Post by rsambuca on 2007-12-08
> **Methuselah said:**
> Thanks a lot for your great help.
One quick clarification: do you mean, the swap should 'find' the swap partition without me doing anything?

Also, will it automatically install a boot manager?
I already have the BSD boot manager but I'm not yet sure sure if it will automatically detect Ubuntu.

Boy, this forum sure does move fast.
I could barely find my thread after returning.

Yes, I meant find.  The 'e' is just above the 'd'.  That is my excuse and I am sticking to it.

Yes, Grub is installed and should detect Windows and add an entry for it.

There is an option in your control panel to automatically subscribe to thread that you have posted in.  Then you just have to go to "Quick Links" and view your subscribed threads to see if anyone has posted.

---

### Post by Methuselah on 2007-12-08
Cool, thanks!
I'm going to try this.

I'm tired of messing with the Live CD and my old machine (300MHz PII with 192MB RAM) is too slow for ubuntu with gnome and all the trappings.

---

### Post by Methuselah on 2007-12-08
Yeah!
Everything worked out, I now have Ubuntu on my hard drive exactly where I wanted it.

---

### Post by rsambuca on 2007-12-08
All right!  The planets must be in alignment or something. :)

---

