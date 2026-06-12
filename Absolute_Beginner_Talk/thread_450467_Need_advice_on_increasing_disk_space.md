---
title: "Need advice on increasing disk space"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by whein on 2007-05-21
I recently got my MythTV setup working, but it's becoming apparent that I'm going to need more disk space.  My girlfriend found out how easy it is to record shows and has gone nuts with the scheduler...  Three tuners and only a handful of over the air channels that come in clear enough, and in the span of less than a week she filled up 80 gigs.  sigh.

Anyway, I have a motherboard with both PATA and SATA capability.  Currently, my PATA is all taken and I don't have a spare PCI slot to add another controller card.  However, I have all four of my SATA slots free.  I'm looking to buy at least a couple nice new 300+GB drives to throw in there.  Not sure if all future drives will be the same size though.  Now, question is how do I configure them for best results?  RAID?  LVM? Other?

My motherboard claims to support SATA RAID0/1/0+1 (I have an Abit KN8-Ultra).  I've heard rumor that sometimes it's easier to do software based raid in Linux (no idea how).  Or just skip it all and set up LVM  (again, no idea how)?  I have one partition (ext3) in my system mounted as / and another (xfs) mounted as /var/lib/ which myth uses to store recordings at the moment.  Best way to cleanly append the new hard drives to /var/lib/ ?  What programs to use, how to do it?
Thanks in advance!
-Will

---

### Post by arvevans on 2007-05-21
Have you considered, or do you have, a DVD writer?  That might allow transferring stored content to removable media and thus avoid having to add more hard disk space.
 [Yes, you do have to consider the potential consequences of recording possibly copyright protected material]

Arv
_._

---

### Post by whein on 2007-05-21
> Have you considered, or do you have, a DVD writer? That might allow transferring stored content to removable media and thus avoid having to add more hard disk space.
[Yes, you do have to consider the potential consequences of recording possibly copyright protected material]

Arv
_._

Actually, I have a DVD writer already installed, but I'm not really keen on that for a couple of reasons.  Biggest one is cost.  Blank media are starting to get cheaper, but still add up quickly for the space I'm looking at.  Secondly, I'd have a whole lot of disks lying around and I'd have to catalog them all and keep them organized and swap out one to put in another...  Gets old fast compared to the nice database and all-in-one-place way that Myth uses.  And lastly, most of what I record will be watch once or twice and then delete forever, so in that case I'd want rewriteable disks, which just increase the headache of #1 and #2.  I'd like to save DVDs for backing up really good shows or movies once in a long while.  On a side note, I'm also having issues playing DVDs without having them skip.  Every couple of seconds the audio and video jump a little.  The drive has DMA turned on and this happens inside and outside of Myth.  Something else I need to track down and fix, but another day.

So back to the original question, assuming I have a couple new SATA hard drives, what is the recommended way to combine all my new and existing space into a single chunk that Myth can use and doesn't make my head hurt?
-Will

---

### Post by hartz on 2007-05-21
I don't know MythTV, but 80 GB is a lot to fill up in a week - can't you tune the quality down a little and save a lot in space consumption?

At any rate, LVM is probably going to be the answer to your question of combining multiple drives into a single "volume".

---

### Post by superm1 on 2007-05-22
As mentioned before LVM will be your answer.  Unfortunately it will be a bit of a tedious process to do.

I'll try to outline the jist of it.  You'll have to get specifics for each of the steps yet though.

1) Install a second hard drive.
2) Format that drive to your favorite file system.  It will only be temporary.
3) Stop backend process 
```
sudo /etc/init.d/mythtv-backend stop
```

4) Copy over all recordings to the new drive
5) Open up fdisk and change the type on the current recordings partition to be LVM (0x8e if my memory suits me).
6) Create a LVM volume group and PV
7) Format the LVM (XFS is ideal for this since you can grow it live)
8) Copy over all recordings from the other drive to the LVM
9) Open up fdisk and change the type on the new drive's partition to be LVM.
10) Add the drive to the LVM group
11) Grow the LVM volume to the new size
12) Grow the XFS file system to the new size

And then you should have a much larger recordings setup.  Only problem with LVM though is that if a drive dies, then the whole group will die.  So hopefully you've got a bunch of stable hardware :)

---

### Post by whein on 2007-05-22
> Only problem with LVM though is that if a drive dies, then the whole group will die. So hopefully you've got a bunch of stable hardware 
Yeah, that's my biggest worry.  Not the end of the world since I only plan to have TV shows and such, but still something I'd like to avoid.  That was why I was debating doing a RAID array using one of the fault tolerant/redundant versions (probably RAID 1).  But I have no experience with RAID and as far as I understand it, the disks need to all be the same size?

Is there any other way that I can have Myth (or at least the database) look in more than one directory for recorded shows?  Set up one folder for recent recordings, and then have an archive on one or more disks that is still linked back to the mysql database containing all the title and plot summary information?  That way if one goes down it only takes with it whatever was on that single drive and not all three drives worth?
-Will

---

### Post by newlinux on 2007-05-22
> **whein said:**
> Yeah, that's my biggest worry.  Not the end of the world since I only plan to have TV shows and such, but still something I'd like to avoid.  That was why I was debating doing a RAID array using one of the fault tolerant/redundant versions (probably RAID 1).  But I have no experience with RAID and as far as I understand it, the disks need to all be the same size?

Is there any other way that I can have Myth (or at least the database) look in more than one directory for recorded shows?  Set up one folder for recent recordings, and then have an archive on one or more disks that is still linked back to the mysql database containing all the title and plot summary information?  That way if one goes down it only takes with it whatever was on that single drive and not all three drives worth?
-Will

For RAID 1 the disks don't have to be the same size, depending on the implementation. Myth .20 is not setup to have recordings in multiple dirs, but the next version is, but who knows when that will be ready to go. You could use MythArchive to archive your recordings in a different spot and then view them through MythVideos.

---

### Post by whein on 2007-05-22
From the MythTv Wiki page for MythArchive:
> The MythTV 0.20 release has a nasty bug which could cause serious file system damage when archiving to raw format and should not be used.
doh!
other than that...  sounds like that would work very well for me.  Keeps all the metadata and stuff.  Anyone out there used this before and care to comment?
-Will

---

### Post by newlinux on 2007-05-22
I've used it only a couple of times (not recently) and it worked well for me, but I didn't archive to raw format, I archived to dvd so I don't know if that bug applied to what I did. Sounds a bit scary.

I know some people over at Mythtvtalk forums use it, but I don't know if anyone has run into this bug...

---

### Post by superm1 on 2007-05-22
> **whein said:**
> From the MythTv Wiki page for MythArchive:

doh!
other than that...  sounds like that would work very well for me.  Keeps all the metadata and stuff.  Anyone out there used this before and care to comment?
-Will
That particular problem is because mytharchive likes to take over the directory that you have set as a temporary directory (chmod 777 and chown and such).  As long as you set it to a safe directory, it shouldn't really be a worry.


I used to use it to archive things with metadata but eventually decided I was much better off just archiving the files myself from a seperate burning app. 

The files that are > 4GB won't meet ISO9660 level 3 restrictions.  So what I did was set up the contrib script that comes with mythtv backend to create a "readable recordings" directory on nfs.  All the files have nice names reflecting show title and recording date/time.  I burn these with an app with udf support then (Nero linux on my laptop)

---

