---
title: "Multiple hard drives and linux..."
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by akross on 2005-06-23
To all~

I apologize if this is something that has been asked before, but I only have a little time left on my lunch.  I am going to be using a PII 300MHz computer with (at least) 128 MB of RAM to learn Linux.  So here is what I plan on doing aside from the obvious learning command line basics and how to find my way through the "easy" stuff.  I want to set up the computer to run as a webserver to host my personal blog and store class files for access anywhere on the internet.  I will eventually have 2 hard drives to work with, a 4 gig currently in the machine, and a 30 gig that I plan on adding after I backup my files and whatnot.  I am anxious to get started learning again (I started with Mandrake about a month ago, and got sidetracked by work and my evening class...

After all of that rambling, my question is this:  Is it better to install the OS and all the necessary applications on the 4 gig drive and use the 30 gig drive as my data storage drive, or the other way around?  I don't forsee the amount of files I will be putting out on the web getting anywhere near 4 gigs, but you never know...

I am assuming that the dual HD setup would work in a similar fashion to a Windows setup, for which in the past I used the larger of the two drives I had available at the time for the OS and the smaller for the data.  Am I right?

Thank you in advance!
Andy (currently the "absolute beginner" poster child)

---

### Post by Ampersand on 2005-06-23
I've got about 3Gb used for system folders. It's probably safest to use the 4Gb drive as /home and the 30Gb drive for the root directory. You'll also need to create a swap partition on this drive (probably around 250Mb).

---

### Post by TravisNewman on 2005-06-23
yeah, the general rule is to have a swap partition that's about twice the amount of ram in your system, though on machines above 512 or so, swap isn't really that important. I used to have a gig of ram before one stick went bad, and using a swap partition only slowed things down.

---

### Post by Lunde on 2005-06-23
[QUOTE=akross]To all~

I apologize if this is something that has been asked before, but I only have a little time left on my lunch.  I am going to be using a PII 300MHz computer with (at least) 128 MB of RAM to learn Linux.  So here is what I plan on doing aside from the obvious learning command line basics and how to find my way through the "easy" stuff.  I want to set up the computer to run as a webserver to host my personal blog and store class files for access anywhere on the internet.  I will eventually have 2 hard drives to work with, a 4 gig currently in the machine, and a 30 gig that I plan on adding after I backup my files and whatnot.  I am anxious to get started learning again (I started with Mandrake about a month ago, and got sidetracked by work and my evening class...

After all of that rambling, my question is this:  Is it better to install the OS and all the necessary applications on the 4 gig drive and use the 30 gig drive as my data storage drive, or the other way around?  I don't forsee the amount of files I will be putting out on the web getting anywhere near 4 gigs, but you never know...

I am assuming that the dual HD setup would work in a similar fashion to a Windows setup, for which in the past I used the larger of the two drives I had available at the time for the OS and the smaller for the data.  Am I right?

Thank you in advance!
Andy (currently the "absolute beginner" poster child)[/QUOTE]
 Depending on the speed of your hard drives, 4gig is a litle to small, but it's do'able. Maybe you should consider partitioning your larger drive into some smaller partitions instead.

OK a suggestion is.. 
I assume your 4gig is a slower then your 30gig, if so I suggest you just use it for backup. Partition your 30gig drive into one 20gig parttion (Ext3 or ReiserFS) in the end and leave a 10gig empty space in the beginning (Primary), Ubuntu will partition this during Install into swap and root. After install, mount the 20gig partition as your /home folder and also link apache www root to a folder under your /home

Now, when you do a system backup, leave out your /home and backup only the root system into the 4gig disk

Also don't store your files directly in your /home/username/ but put your files in a subdirectory. then backup your /home and leave out your /files and /www so it's only your users configuration files that gets included in your backup, this should probably also fit in the 4gig disk. 

Now you can at any point during your learning period recover your settings if you screw up something.. just make sure you don't mess with the /boot directory

Maybe 10 is a litle big, but make sure the partition never gets to full, have a lot of empty space on tht root and leave enough space to be able to test various software as this is for learning. 

Backup howto:
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

---

