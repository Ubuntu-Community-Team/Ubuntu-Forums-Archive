---
title: "system setup for new install"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by sts71 on 2006-09-26
Hey Everyone,

Ive trawlled thru pages trying to find answer to this question but havent really found answer yet and it might help ut someone like me.

I have two pc pc1 = p4 i use for work and dtp
pc = p3 backup system, plus one I try programs on and then I full install on the pc1.

Works got me having to learn stuff, unix etc and some have suggested learning linux long story that one.

What I was thinking of doing was installing a fresh 80g hd in the pc2 as a second drive so it had two 80g drives, and installing linux on that second drive, ie dual boot?

OR, getting a cheap used p3 and putting that fresh 80g drive and loading ONLY linux on that.

Those have used both ideas, ie dual boot and seperate pc, have you had any issues with dual, is it better to have a totally linux pc. And if its a dual system, how do you get to the windows partition and run that? Do you have to reboot the machine totally to switch OS?
I bought the ubuntu software with a magazine that had three ubuntu disksm anyone used these? (mag was called get started with ubuntu linux)
Many thanks in advance, and great to see such a great forum.

Cheers

Steve

---

### Post by sts71 on 2006-09-26
[http://ubuntuforums.org/showthread.php?t=265103](http://ubuntuforums.org/showthread.php?t=265103)

just saw this one after posting, sorry, sorta answers my questions but now have a further one, do i need to create a FAT partition to share data files with windows when I eventually get a network going, and how much a nightmare is putting a linux machine on my router to share data?

Very excited to start this project and thought it best to read up first before I loose any more hair then I already have
thanks again for reading these questions

Steve

---

### Post by dbd on 2006-09-26
Linux can read NTFS with no problems, but has problems writing to NTFS partitions, so it may be a good idea to have a FAT partition to share data. Just remember that FAT is really not very good, so you don't want all your linux root or home partitions to be FAT, just make an extra FAT partition.

However, this program can apparently allow windows to read linux partitions, so that may help (I've never used it, just heard about it on these forums):
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Putting your linux machine on your network to share files with windows is not particularly hard, see here:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by ajgreeny on 2006-09-26
99% of installs using a wired router find the connection without any problem.  Just occasionally a network card presents driver problems to linux,but it's very unusual.  Wireless routers can be more difficult, and will mainly depend on the chipset of your wireless adapter card, not the router itself, which simply produces signals;  it's picking up the signals which can be the problem.  There is plenty of info on the forum and various wiki's to help, so do a search and you should find some helping hands about.

---

### Post by sts71 on 2006-09-30
Ok have tried the single drive install with a new hard drive, the ubuntu screen comes up but takes over 40mins before anything happens.
That route I gave up on,
now trying to install with new drive drive as teh d drive and teh damn ubuntu disk doesnt boot, Ive tried two different disks to no avail, just the splash screen comes up and nothing else.
The pc is p3/500 256ram and doesnt allow in the bios for cd boot,(its an ibm)
Any suggestions before these disks become coffee cup coasters and I have to live with Bill G??
And Ive been at it most of today and its driving me nuts.
Steve

---

### Post by sts71 on 2006-09-30
oh and the disks im trying to install from are ubunti disks, one from a 3 cd set and other was from mag cover, the ubuntu 606 release if that helps any.

---

### Post by hyper_ch on 2006-09-30
you could also use samba for a general shared network drive through the whole network :)

Regarding the CDs.. you can download them easily and burn...

Ubuntu (Gnome Desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Kubuntu (KDE Desktop)
[http://www.kubuntu.org/download.php](http://www.kubuntu.org/download.php)

Xubuntu (Xcfe Desktop)
[http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/](http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/)

You can download either desktop version... the difference between them is that they feature by default different desktops. However you can quite easily add the other ones if you want to test them also:

```

aptitute install ubuntu-desktop

```

```

aptitute install kubuntu-desktop

```

```

aptitute install xubuntu-desktop

```

---

### Post by RRS on 2006-09-30
> ....doesnt allow in the bios for cd boot...
Doesn't sound like the problem is with your discs. If the system can't boot from the cd then you won't be able to install from it either.

I seem to recall that there's a way to install over a network connection.

I also think you can make a floppy boot disk that you can use to boot the computer from the cd as a work around to the bios issue.

I'm afraid these are methods I've never looked into very deeply but I'm sure I've run across them outlined here in the forums so it should be worth a search.

You might also want to check one of these sites, I know the first one has some info on boot floppies.

[http://users.bigpond.net.au/hermanzone/index.htm]("http://users.bigpond.net.au/hermanzone/index.htm")
[http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php")

Good Luck :)

---

### Post by sts71 on 2006-09-30
thank you appreciate the advice, Ill check out those boot floppys and if I get a solution will post it here.

Cheers

---

### Post by RRS on 2006-09-30
I just ran across this in another thread;
[https://help.ubuntu.com/community/SmartBootManagerHowto]("https://help.ubuntu.com/community/SmartBootManagerHowto")

Don't have a working floppy drive to test ot myself but it looks like what you need.

---

