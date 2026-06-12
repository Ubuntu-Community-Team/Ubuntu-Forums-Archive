---
title: "Seeking recommendation for new install"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by rexwalterson on 2007-04-30
Greetings,
I would like to install Edubuntu LTS on my primary home PC and then convert a couple old pc's to wireless thin clients that connect via my Netgear router.  My wife and I (mostly my wife) home school our children and I would like to provide them access to some of the programs bundled with Edubuntu.  Plus I really like open source software and would like to kick the Windows habit.

The box I want to use as the primary PC is currently running XP which I have installed on a Western Digital 80 gb IDE drive.  The system also has two 300 gb Maxtor SATA drives running as RAID 1.  The MoBo is an Asus K8V SE Deluxe with an AMD 3000+ CPU and 2gb of RAM.   

Initially I was thinking about partitioning the 80 gb drive to make the system a dual boot machine with Linux and XP both installed on the 80 gb drive.  The reason I initially set the system up the way it is, was because I assumed Windows would get all crufty after awhile and would need to be reinstalled.  So I wanted all my docs, pics, etc stored on the RAID 1 drives and away from Windows.  

But now I'm wondering if it wouldn't be smarter to install Edubuntu on one of the 300 gb drives, set it up as RAID 1, and include an NTFS partition for my Windows storage as I and my family make the transition to Linux.  If I do have to continue to use Windows for some apps, and ever have to do a clean install on that drive, I assume I'd be better off if Edubuntu were running on a different drive altogether.

I'm a real novice with Linux and only have enough knowledge about Windows to be dangerous.  For all I know, maybe it isn't possible to set up my box to either boot to Windows from one drive or to Linux from another.  So suggestions and recommendations from those of you with more knowledge and experience would be greatly appreciated.

---

### Post by mikeyphi on 2007-05-01
Don't think it will make too much difference which way you choose!!

When you install ubuntu it will see the XP and give you a dual boot regardless of which drive it's installed on! But, probably, ubuntu will be easier to install on your IDE drive.

There will be a (minor) issue later on when you remove XP - you will need to change the Grub, otherwise both os's will be fine!

---

### Post by AAM on 2007-05-01
the other option is to install Edubuntu on all the machines and use NFS to access the 'central repository' on your server. All machines will need access to net to update. You have a reasonably large number of choices including a network feed to thin clients, whatever.

My 9 year old daughter uses a dual PII Kayak workstation with 512MB RAM, a Nvidia 5500 video card and 80GB HDD with an old 15 inch LCD screen. Bit slow when starting programs but enough for the next 12-18 months while she learns to configure, etc. At least I can put off the BIG purchases until its needed. My 13 & 15 y.o's use 800-900MHz PIIIs which work very well. One is really giving The Gimp a hammering and hasn't started complaining about speed yet. None of this stuff cost me much and serves a purpose .

---

### Post by rexwalterson on 2007-05-01
Thanks for the replies.  Using the old PC's more as workstations instead of true thin clients makes sense.  At some point I'd like to have a fanless mini-itx (like a koolu) mounted on the back of an LCD TV.  That would save a lot of space in our cramped living quarters.  But there aren't funds for that kind of setup right now.  

I'm still undecided about how to set up the main PC/Server.  Part of my thinking has been that Linux will be far more stable than Windows, so having the OS and the file storage together on a RAID 1 setup, I'll be in excellent shape in terms of a stable system with a mirrored backup drive.  That's the way I'm inclined to go.  I'll have to move the files that are currently on the RAID drive to the 80gb, but I have enough room left on the smaller drive to accomplish that right now.  After I have the 300 gb drive set up with Edubuntu and RAID 1 working, I can move the files back to the 300 gb drive.  

That's what I'm thinking anyway.  Don't know if it's the best way to go or not.

---

