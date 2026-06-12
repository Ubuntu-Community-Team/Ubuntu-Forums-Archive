---
title: "RAID 5 Idiots guide please"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by itzpapalotl on 2007-06-28
Soooo....... go this nice newserver which is going to be the  backbone of a k-12 school's network.

Got my 6.06 dapper server disk.

Got 4 250gig serial ATA disks. 

Now, what I want is a 750 gig RAID 5 array.

Only... I don't get it.

I'd like:
/boot 100 meg
/ maybe 5 gig
/swap 5 gig
/home 370 gig
/var 370 gig + leftovers.

Now...

So... I 've looked up"RAID 5" I've looked up RAID.. I've googled and goggled and I can get as far as having a single 750 gig device, but I can't install on it..  I think I'm going a this the wrong way.
Anybody know where the idios guide to RAID 5 in Ubuntu is (I want to use he software RAID system built in to Linux. My "hardware" RAID is not really a hardware RAID anyway.)

---

### Post by lwh on 2007-06-28
Hi

Try to have a look here: [http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html) (RAID1 but it basicly the same you need to do)

But basicly boot your server from the installation CD, and when you get to the disk-part chose manual partisioning, you need to create the diskformat for software raid, for each disk that need to bee part of the software raid.
After this you are able to create softwareraid partision, which you then partision as you would an ordinary disk.

---

### Post by Yoooder on 2007-06-28
I have had success using several disks pooled via RAID-5 with LVM2 running on top of the multidisk device.

Basically you setup your RAID, then setup LVM2 on your raid device.  The big benefit of using LVM is that you can easily add/resize new partitions to the pool without the usual partitioning constraints.

---

### Post by itzpapalotl on 2007-06-28
Okay... Thanks gang.

So I'm straight in my head..
First turn them ALL in to one big RAID 5 volume...THEN partition that.
THEN install on top of that..
Check.
Also Thanks for the info about LVM. I'm going to give it a go. I'll check back with either success (hopefully) or failure. 
Meanwhile. If  anybody else has more info...

Thanks again folks. You all are the best.

---

### Post by itzpapalotl on 2007-06-28
Rightio then.

Okay. Set them all up (all 4) as Phisical dive space for hardware RAID.

Got a new device:
RAID5 devic #0 750.2 G software RAID device.... looking good so far...
Now. under that I have #1 primary 750.2 GB.

So. Now I go to resize it, chop it up, set up some partitions etc...
choose the resize option.
Accept the whole write to disk thing.
Pick a size. (lets do the boot. so 100 MB) hit enter.
Chews on that for about 30 seconds and then:
and I quote:

"Error informing the kernel about modifications to partition /dev/md/0p1 -- Invalid Argument. This means Linux won't know about changes you made to /dev/md/0p1 until you reboot -- so you shouldn't mount it or se it until after rebooting.

ERROR!!"
 I can then choose to ignore or cancel or go back.
What I can't o is install Ubuntu....
Ack

---

