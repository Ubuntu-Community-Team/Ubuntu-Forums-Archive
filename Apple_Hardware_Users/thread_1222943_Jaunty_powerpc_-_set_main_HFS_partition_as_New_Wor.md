---
title: "Jaunty powerpc - set main HFS partition as New World... trying to recover data."
date: 2009-07-25
forum: Apple Hardware Users
---

### Post by tandemocracy on 2009-07-25
Hi folks,

I'm having a bit of trouble with Synaptic on an install of 9.04 on an old Powerbook G4.

I desperately need to install testdisk in order to recover some lost files due to a partition editing disaster, but i can't seem to get the repositories to update through synaptic. I'm getting a 404 at /jaunty-security/main/binary-powerpc/packages...

I can navigate the webs, and it appears that the other repositories connect and download, but i need these to install testdisk, don't I?  

I downloaded a .deb and the install failed due to an unsatisfiable dependency...

I need guidance.  A link, a hint, something.

This is a friend's wife's G4 with recent wedding photos and whatnots... not too much data.

Anyone?

---

### Post by tiresia on 2009-07-28
It looks like there are broken dependencies for testdisk in PPC-Ubuntu since Hardy
[http://packages.ubuntu.com/search?keywords=testdisk&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=testdisk&searchon=names&suite=all&section=all) (but you can still install testdisk in Dapper...)
In Debian it looks different. Here you can find the list of the dependencies
[http://packages.debian.org/lenny/testdisk](http://packages.debian.org/lenny/testdisk)

But I would have a question: if you want to recover data from the HD in the PB, you shouldn't install stuff on it! You should use another computer and run testdisk from there (connecting the PB's HD to it)

---

### Post by tandemocracy on 2009-08-01
Thanks Tiresia for your response!

At that time I was trying to install while running from a livecd and couldn't get the repositories to load for ppc...

I didn't want to write anything to the disk at all.  But it is noteworthy to know that I installed jaunty for ppc on the G4 from a livecd, which shrunk the original 40gb partition down to 25 gb.  Then it formatted the raw drive with ext3 for ubuntu... during the prompts  for the partition changes, I mistakenly chose the main HFS partition as the "Newworld" partition, which effectively formatted that partition.

So what i have is a functional Jaunty and a completely f-ed up OS X partition of 25gb size.

The owner would desperately like to retrieve a resume and some photos... 

I used photorec and restored some 100,000 files from it, and i also have a dd image of the 25 gb partition, but the resume is a .doc, and i have none of those in my photorec results.

I also tried DiskWarrior to no avail, it won't mount the disk.

I'm ready to reinstall OS X on this thing, but that resume is important.

Any suggestions for a utility (mac, linux or even windows if it can read from a dd file) that can help me find strings in raw sectors or in some other way help me restore the files from this image or from the drive?

I'm failing, and running out of time...:confused:

---

