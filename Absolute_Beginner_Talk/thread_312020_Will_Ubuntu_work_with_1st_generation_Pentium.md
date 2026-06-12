---
title: "Will Ubuntu work with 1st generation Pentium?"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by WilliamK1974 on 2006-12-03
Hello everyone,

This is my first post on this forum. I've long been interested in building a Linux desktop system in part because I enjoy homebrewing computers. Plus it's free!

I've assembled some hardware to use for an Ubuntu system, but am still missing a couple of pieces. No big deal.

We have my wife's old Pentium I setup, and it still seems to work. None of the components are dead.

Would Ubuntu run on that? The biggest advantage to using it would be that it's here and paid for. The disadvantages could be its age and that its motherboard is limited to rather small hard drives. I tried to install a 40GB drive a couple of years ago, and the system wouldn't recognize it. I have the 4 or 5 GB drive currently installed, as well as an extra 3.1 GB drive that could be configured for extra storage.

This might tide me over until I can finish building my planned system, unless it's a bad idea or waste of time. Any suggestions would be welcomed.

Thank you,
-Bill

---

### Post by atoponce on 2006-12-03
It will run, but it's going to be sloooow.  I run Ubuntu-server on a Pentium 450Mhz with 192MB RAM, and even with a light window manager, it is still slow.  Eventually, I just ditched the X server, and left it just for remote SSH.  But it's a server, not a desktop, so...

---

### Post by Mimsy on 2006-12-03
I would try Xubuntu, if you're going to use an Unbuntu version on it - it is a lot lighter graphically, and requires less ram. It will probably still be slow though. Out of curiosity, how much ram does the old machine have?

/Mimsy

---

### Post by yabbadabbadont on 2006-12-03
The processor should be supported, and you can probably get enough disk space installed, but the big thing is the memory.  I think xubuntu (one of the lighter versions of Ubuntu) requires 192MB.  The normal desktop install requires 256 and a server install only 64.  See the Dapper release notes for details:  [http://www.ubuntu.com/download/releasenotes/606](http://www.ubuntu.com/download/releasenotes/606)

---

### Post by louieb on 2006-12-03
P1 200 128 mb ram. Slow but servicable.
 Have tried Ubuntu, xUbuntu, Puppy,  DSL and Slackware on that machine. For a person new to Linux try any of the above but Slackware (not newbie firendly) or Ubuntu (to slow) .  Its an ok box to play with linux on. 
I have a 4 gig and a 3 gig drive on mine. It dual boots XUbuntu and puppy.

---

### Post by NeoGreen on 2006-12-03
Which Ubuntu are you planning on installing?  I would try to install an older  version of Ubuntu maybe 5.10 or less.  I have a Pentium II running Ubuntu 5.10 and it runs pretty good.  :)

---

### Post by PurplePenguin on 2006-12-03
I know this is an Ubuntu forum, so I'd hate to advertise for the other guys, but I honestly think that your system would do a lot better with something like Puppy Linux.  The latest version is very easy to install and has wizards for *everything*.  It would run at normal speed on your old computer, I think.  Damn Small Linux is similar, but (although I haven't tried the latest version that just came out) is far less intuitive.  

Ubuntu's great, but as the others have mentioned, needs a bit more memory to run well.  

The good news is that old computer parts are quite easy to come by.  I've been given a Celeron 600 and a P3 by people that bought new computers and just wanted to give the old ones away.  If you put the word out among friends and family, you might not have to wait long before somebody you know upgrades and doesn't want their old hardware! :D

---

### Post by nightwolf2k5 on 2006-12-03
i got a p5 550mhz.. with 128 ram(arrgg!!).. i'm running win xp stripped edtion.. works ok.. but is a little slow.. actually.. very slow.. will puppy linux be good for it? i kinda use that comp to like download and stuff cuz it uses very little power (550 mhz.. )
so.. will i get like a torrent client on that? and ntfs write permission?

---

### Post by Peepsalot on 2006-12-03
There is a project called [Fluxbuntu](fluxbuntu.org) that I think is aimed at being very lightweight, so maybe older processors can handle it better.

Fluxbox I think is lighterweight than Xfce(Xubuntu).

However, I haven't ever tried this distro, so I don't know much about it.

---

### Post by WilliamK1974 on 2006-12-03
Someone asked how much memory the old machine has. I booted it up a few hours ago, and forgot to look. But it's no more than 512MB, and might be as low as 256MB. The harddrive's only 2.5 GB as well, but that can be changed. Seems like there are places out there to buy new or used harddrives that are less than 20GB.

I'll keep getting parts together for an Ubuntu machine, and will look into getting Puppy Linux for the older one.

Thank you,
-Bill

---

### Post by Mimsy on 2006-12-03
I have 256 Mb of ram on the machine I am typing from right now. It runs Ubuntu 6.06 with Gnome without any difficulties whatsoever. 2.5 GB of harddrive space is enough for Ubuntu, I don't think you have to worry about that part. The ram is usually the bottleneck, but it looks like you're covered there.

If the machine runs Windows right now you should be able to find the amount of RAM through your system manager. In XP it's in Control Panel -> System -> General. I doubt it would be XP on such an old hard drive though :)

Xubuntu needs 192 MB of ram to run, and you need to use the alternate installer, if I remember other forum posts right. 

Good luck!

/Mimsy

---

### Post by PurplePenguin on 2006-12-03
> **nightwolf2k5 said:**
> i got a p5 550mhz.. with 128 ram(arrgg!!).. i'm running win xp stripped edtion.. works ok.. but is a little slow.. actually.. very slow.. will puppy linux be good for it? i kinda use that comp to like download and stuff cuz it uses very little power (550 mhz.. )
so.. will i get like a torrent client on that? and ntfs write permission?

According to [the Puppy entry on Wikipedia]("http://en.wikipedia.org/wiki/Puppy_Linux"):

> When the operating system boots, everything in the Puppy package uncompresses into a RAM area, the "ramdisk". The PC needs to have at least 128M RAM (with no more than 8 MB shared video) for all of Puppy to load into the ramdisk, however it is possible for it to run on a PC with only about 48 MB of RAM because part of the system can be kept on the hard drive, or in the worst case, left on the CD.


I'm sure you can get a torrent client running on it.  [This]("http://www.murga-linux.com/puppy/viewtopic.php?p=79318&sid=fe9d2e4b0a75e597d37b3a51d4ba7d26") looks like one in Puppy's package manager format, actually.

It's worth a shot downloading it and giving it a try, anyway.  I think that the CD image is about 60 MB or something - quite a small download.  If you don't like it, it's not as if you've wasted a long time downloading or anything! :)  It's a live CD, too, so you can play with it and it won't change anything on your hard drive.

I have a ton of fun downloading, burning and trying out new live CDs.  It's amazing to see what each distribution does to make itself unique. :)

---

### Post by atoponce on 2006-12-04
> **PurplePenguin said:**
> I know this is an Ubuntu forum, so I'd hate to advertise for the other guys, but I honestly think that your system would do a lot better with something like Puppy Linux.  The latest version is very easy to install and has wizards for *everything*.  It would run at normal speed on your old computer, I think.  Damn Small Linux is similar, but (although I haven't tried the latest version that just came out) is far less intuitive.  

There is nothing wrong with advertising for the "other guys".  We need to realize that we are all on the same team, even if we do have different tastes in distributions.  Sometimes, Ubuntu just isn't the perfect fit, so as a community, I would hope that we can recognize this, and help find the distro that best suits the users needs.

With that said, given the information of this certain computer, I would most definitely recommend Damn Small Linux or Puppy Linux.  Both are lightweight, super fast, and I think will suit your needs well.  If you want to try Ubuntu, then you should try Fluxbuntu (Ubuntu with the Fluxbox window manager).

---

