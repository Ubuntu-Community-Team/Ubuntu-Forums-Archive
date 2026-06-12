---
title: "How do I move my system from an IDE (PATA) hard drive to a SATA hard drive"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by bwallum on 2008-01-02
I have found a different thread that sort of covers this issue but my request is more specific so it is posted here as a new thread.

I have a 64bit machine that has both PATA and SATA capability. I have Ubuntu 7.10 set up on PATA harddrive and then decided I needed more hard drives so bought a couple of SATA harddrives. What I want to do is have two SATA drives in my existing box and use the PATA harddrive in a new build.

I then set up 7.10 on a SATA drive, all sitting in the same machine and all doing away nicely until..

Groups seemed to be replicating them selves and my SATA installation gradually cracked up. My router was showing the internet link up continously and it felt as though someone was taking over my machine. I fiddled until I had no gui and an error message telling me GDM was missing.

What I would like to do is transfer the entire system that is good and on my PATA hard drive, to my new SATA harddrive.

I can do this with a fresh install and knife and fork all docs from one to the other but wondered if there was a simpler, less prone to memory (mine) lapses, way to do the job.

??
Bob

---

### Post by nick_h on 2008-01-02
I fresh install would be the best way to go about it.  All your documents will be stored under your home directory.  You may have made changes to some files in /etc but probably not too many.

---

### Post by gn2 on 2008-01-02
You can use a CloneZilla live CD to clone one hard drive to another: [http://clonezilla.sourceforge.net/clonezilla-live/](http://clonezilla.sourceforge.net/clonezilla-live/)

---

### Post by lamalex on 2008-01-02
+1 for clonezilla!

---

### Post by LowSky on 2008-01-02
found alot of good stuff here

[http://en.wikipedia.org/wiki/Disk_cloning](http://en.wikipedia.org/wiki/Disk_cloning)

here are some open source and freeware options

Freeware
Trinity Rescue Kit 
DriveImage XML 
partition-saving 
XXCLONE 

Open Source free software
FOG - Free OpenSource Ghost (SourceForge) 
Clonezilla (DRBL) 
PartImage 
g4u - ghost for unix 
G4L Ghost for Linux Boot CD 
LRS Linbox Rescue Server

---

### Post by bwallum on 2008-01-03
Thanks everybody. I liked the idea of CloneZilla, downloaded it, created a bootable disk and loaded it. Then bottled out because I was unsure of what I was doing.

I used Simple Backup in the end to backup

/var/
/home/
/usr/local/
/etc/

these were offered as defaults. I backed up onto my second SATA drive from the PATA, then fresh installed 7.10 onto my first SATA drive. I then restored from SATA2 to SATA1. (I kept the owner and password consistent for ease of access once reinstalled).

'/home/' restored a treat. '/var/' and '/etc/' hung for some reason. However all now works, almost. I need to recover my Evolution mail and contacts.

I am now trying to find out where Evolution keeps this data by default. I never set up anything special with it so expect to find everything in a default location. It doesn't seem to be in any of the above directories.

Thanks again,
Bob

---

### Post by nick_h on 2008-01-03
> I am now trying to find out where Evolution keeps this data by default.
Evolution keeps its data in your home directory under ~/.evolution/mail/local

At least with a fresh installation you won't have copied any problems you had with your old installation.

---

### Post by bwallum on 2008-01-04
Thanks Nick, I have Evolution back now.

Regards
Bob

---

