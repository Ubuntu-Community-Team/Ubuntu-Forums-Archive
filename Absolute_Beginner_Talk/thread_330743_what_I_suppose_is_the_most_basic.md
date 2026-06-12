---
title: "what I suppose is the most basic"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by uuu on 2007-01-03
So I got my ubuntu disk in the mail...and I put it in the primary cdrom drive, reboot, and tell the computer to boot from disk...and it will only let me install on the front end of the drive, there are no partitions yet, and it looks like I have to allocate some space for the root directory?  What am I doing? anyone know anything?

---

### Post by Shatrat on 2007-01-03
Is this a brand new computer with an unformatted disk? I believe that the new Edgy installer will partition and format disks and the Dapper installer won't, but I've only had to install once.  I haven't messed up often enough to have to memorize this distributions installer yet.

Basically, if you arent wanting to dual boot or anything, all you really need is 2 partitions on your disk.  One small 1gig or so partition for your swap, and the rest of the disk for your filesystem, /

Hopefully someone more familiar with the installers will fill you in on how to do that, although I think we need to know which version you have. 6.06 dapper or 6.10 edgy

---

### Post by maniac_X on 2007-01-03
How big is your harddrive(s)? 
Do you plan on duel-booting with Windoze?

If you booted from the Live CD, it doesn't install to your drive yet.

---

### Post by uuu on 2007-01-03
Yeah, I'm intending to make a dual boot system for the time being

it allowed me to create a partition, but there had to be two of them, presumably for the swap files, I think it told me it was for the root directory, but w/e

It would only create partitions that started at the beginning of the disk, where windows was, and I don't really want to install over it, I want to put up my partitions and have ubuntu on the back end of the disk

the harddrive is pretty small, it's 80 gigs, but I'm just feeling out linux so I thought it would be enough

the computer is about 2 years old...

---

### Post by bodhi.zazen on 2007-01-03
First, defragment your windows partition.

Next, backup you "critical data". Data loss is unlikely, but why risk it ?

Then you will need to resize and install Ubuntu.

Here is a guide:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by uuu on 2007-01-03
thank you for the link...I'm up and running now...hear me roar!!!

---

