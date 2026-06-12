---
title: "Windows XP to Ubuntu"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Wotching on 2007-03-18
I currently run Windows XP, with a 250gb HDD partitioned into 2 partitions: one for the OS [70 gb] and another for my files/data [160gb].   I would like to install Ubuntu on my computer, as I'd rather not have to use a live CD.  I chose install in Ubuntu, went through the options, and got to step 5: partitioning.  Which option should I choose if I DO NOT want my data erased?  Basically, I'm just not sure which of those options would require me to back up my files and which wouldn't.  The options are (vaguely): divide the bigger partition into 2 partitions, completely erase the HDD, another option that I can't remember, and Manually edit partition table.

The first one looks most promising, but again; which one will not require me to back up files, if any?  Thank yoooooouu!

Edit: Just to make sure, I want it to be configured so I can dual boot Windows XP and Ubuntu.  (IE, while the computers is booting, I can choose which one to boot from.  I don't want XP off of my system)

---

### Post by oilchangeguy on 2007-03-18
how much of the 160gb is free space?

---

### Post by annda on 2007-03-18
DEFRAGMENT your windows partition first (important!) and let the ubuntu install use/resize the win partition. just DON'T erase the whole disk and you will be fine.

---

### Post by Wotching on 2007-03-18
There's about 100gb free on the 160gb partition.  Thanks annda; are you sure about using the win partition?  There's only 30gb free on it, out of 70.  Plus, I have an automatic defragmenter.  Should I do a regular defragment anyway?  I just want to make sure you're positive that I should choose the first option.  Thanks.

---

### Post by oilchangeguy on 2007-03-18
the choice is yours. but if it were me, i'd use the 100gb of free space and let ubuntu split that in half.

---

### Post by mdsmedia on 2007-03-18
Is there a reason you don't want to backup your data?

If no good reason, I would backup your data JUST IN CASE something goes wrong with the partitioning. If all goes well with partitioning, which it USUALLY does, there shouldn't be a problem, but all you need to do to mess it up is to make a wrong turn.

I would recommend backing up your data just to be sure.

Also, before partitioning, certainly do a normal defragment of your drive so that any partitioning will not cause problems with fragmented data...and so you have a clean area to install Ubuntu.

---

### Post by Wotching on 2007-03-18
Well, it seems that it won't let me resize the win partition.  The only option is to resize the other one, with 100gb left.  Guess I'll do that, and split it in half.

But seriously.  I'm terrified that it's going to delete my music, TV shows, movies, etc., most of which I do not have backed up!  Resizing the partition should not delete anything, right?  It'll just move everything to a smaller partition?

Edit, in response to MDSMedia: Ok, I'll back up.  It's just that I have many gigabytes worth of stuff.  I guess I should do it anyway, even if I don't install ubuntu, in case my HDD fails some day.  =P  thanks.

---

### Post by mdsmedia on 2007-03-18
> **Wotching said:**
> Well, it seems that it won't let me resize the win partition.  The only option is to resize the other one, with 100gb left.  Guess I'll do that, and split it in half.

But seriously.  I'm terrified that it's going to delete my music, TV shows, movies, etc., most of which I do not have backed up!  Resizing the partition should not delete anything, right?  It'll just move everything to a smaller partition?

Edit, in response to MDSMedia: Ok, I'll back up.  It's just that I have many gigabytes worth of stuff.  I guess I should do it anyway, even if I don't install ubuntu, in case my HDD fails some day.  =P  thanks.It's a good idea to backup your data anyway, but if you're resizing the partition there is always the chance something could go wrong. At least then I could say "I told you so" ;)

---

### Post by Michaelt74 on 2007-03-18
Check this out, it's a very useful newbie guide.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by undertakingyou on 2007-03-18
Another thought.  Why partition off a big chunk?  I have ubuntu running on just 20 GB's and it doesn't take up even a quarter of that.  I have a lot of documents on another partition (using NTFS-3G) so that later windows can see it to.  Then I don't have to worry about it.

---

### Post by Wotching on 2007-03-19
Well, the Ubuntu installer won't let me choose less than 40% of the drive; 40% happens to be about 40gb.  Oh well.  I'm currently trying to back up my stuff, which has become a higher priority.  
I am having that oh-so-cliche problem with not being able to format my backup above 137GB.  It is a Maxtor 500GB HDD, and I put it in an external Adaptec enclosure.  Any help?  I've tried using Maxblast to delete the partition and reformat it, but nothing will let me get the drive to the full capacity.  I have XP SP2, and 48 bit LBA is enabled.

---

### Post by airtonix on 2007-03-19
try booting into the livecd with it attached and then use gpartd to do the partition dance?

---

