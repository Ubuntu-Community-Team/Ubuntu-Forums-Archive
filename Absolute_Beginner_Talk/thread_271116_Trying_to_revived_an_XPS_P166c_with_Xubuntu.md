---
title: "Trying to revived an XPS P166c with Xubuntu"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by JedThrow on 2006-10-04
Hi,

These forums are great!  I haven't found an answer yet, but I am learning alot!
Okay, I have an ancient Dell XPS P166c Pentium machine with 96MB of RAM and two 3GB drives.  Can I run Xubuntu on this machine?  I have the Alternate CD and I am stuck at the partitioning part.  What partitions should I make and where?
:confused:

Thanks!

---

### Post by bluefrog on 2006-10-04
the only to find out (am using gnome and don't know about xubuntu requirements) is to install it.

regarding partitions, isn't there the possibility to let the installer autopartition? If yes just let it do it.

James

---

### Post by odinfromvalhalla on 2006-10-04
hey,

i think you could run xubuntu on that machine. i have tested XFCE once, on a slackware and it took about 50MB or RAM. so you should be good with waht you have.

---

### Post by Sef on 2006-10-04
I would just partition the whole hd.

---

### Post by JedThrow on 2006-10-04
I have two(2) 3GB drives and the auto partitioner got confused or something and I found myself in an endless loop.  Kept taking me back to the partitioner.  Soooooo, I was thinking of trying to manually do the partition.

---

### Post by JedThrow on 2006-10-04
Sef,

As what, specifically?

---

### Post by bluefrog on 2006-10-04
ok, basically you need one partition mounted as / and one partition (200MB) for swap

James

---

### Post by JedThrow on 2006-10-04
Thanks, James!

Can I put the swap on the second drive(200MB) and use the rest for /home?  And the "first drive" could be "/"?  Do I need a /Boot?

---

### Post by bluefrog on 2006-10-04
yes to the first question and second eventually to the third.

/ and swap are compulsory. the rest is optional.

James

---

### Post by JedThrow on 2006-10-04
Thanks for the help!  It will take a while, but I will tell ya how it turns out.

---

### Post by JedThrow on 2006-10-04
Well, I am stuck in the same loop.  

Doing the Text install with the Xubuntu 6.06.1 Alternate CD.

I tell it my language, keyboard type and then it detects hardware (doesn't recognize my 3Com cards, which doesn't worry me).  

Next it starts up the partitioner.  It says that it will make a swap and / on the first drive, which is actually 2.6GB.  It asks me to confirm the partitioning and then starts partitioning.  Then it take me back and asks if I want to partition more.  I say No.

Next it starts up the partitioner, again.](*,)   So, I wait till  it loads and say I want to <go back>.  It takes me back to a task list and I try to pick the next task, which is Time Zone.  All seems to go well and then....

Next it starts up the partitioner....

What am I missing?!?

---

### Post by K.Mandla on 2006-10-04
Hmm. A couple of ideas. ...

Try hitting escape after the drive is partitioned and formatted, and skipping forward in the installation. If you're just stuck in a loop but the drives are ready, you might be able to finish it anyway.

If that doesn't work, try unplugging the second drive and just doing a default installation first. If that finishes OK, then there's some sort of confusion between the drives.

Lastly, wipe the entire disk start to finish with something like [Killdisk]("http://www.killdisk.com") and start with a clean slate. I'm wondering if a messy partition table or something might have the installer confused.

Anyways, just some ideas. Good luck! ;)

---

### Post by JedThrow on 2006-10-05
Thanks for that last post!  I have detached the smaller of the drives leaving the 3.2GB Master on IDE Primary.  Bios detects it and the installation of Xubuntu does as well.  It sends me into a loop again.

I have not found a version of Linux Live to get running so I can completely wipe the drive.  I am currently trying to run Puppy just so I can wipe the drive.

Are there an floppy sized utilities that might help?  Or maybe a VERY LARGE MAGNET!!!

:)

---

### Post by JedThrow on 2006-10-20
Well, after trying for several hours, I decide to take out the contents of the tower, but them neatly in the dumpster and made a squirrel nest out of the rest.:p   

Thanks for everyone that helped me and I have succesfully installed Ubuntu Dapper on a Compaq Desktop 4000.

---

