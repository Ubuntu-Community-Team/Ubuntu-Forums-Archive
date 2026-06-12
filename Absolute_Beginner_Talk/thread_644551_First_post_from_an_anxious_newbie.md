---
title: "First post from an anxious newbie"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by mispelt on 2007-12-19
Ever since Vista came out, I've been thinking about switching from XP to Ubuntu (go figure). I downloaded the Dapper live CD, but held off on installing because I'm using a laptop, and I read my wireless card (Broadcom) was known to have problems playing nicely. I meant to try again with Fawn, but I forgot and missed it completely.

Having heard that Gibbon could fix the wireless problem with a few clicks (from a wired connection, of course) I started feeling the Linux Itch again. I’m very much the learn-by-tinkering type, and the Live CD isn’t cutting it. I want to install Gibbon in a very small partition (Maybe 6GB, max), so I can play with it and see if it’s really for me, but unfortunately, I’ve never formatted a drive or changed an OS (I once upgraded from Win ME to XP, but I don’t count it), and frankly that’s something I don’t feel comfortable with learning on the fly.

Of course, I won't try anything until I copy everything to an external drive, but I was wondering if anyone had any advice for me. Right now I’m a little child who wants to sit on Santa’s lap, but is equally terrified by the huge man in the bright red suit. I just need some encouragement.

Also, my end goal is to have a dual-boot system so I can use Linux and anyone else can use Windows if they choose. I’d like to have a partition with the Linux system files, one with the Windows files, and a third for downloaded files – songs, videos, and such – that both OSes can draw from. Is that even possible? Can Linux be made to play nicely with NTFS, or vice-versa? Will I have to have wine running at all times?

I’m sorry this is so long, but like I said, I’m anxious. I just need someone who knows what they’re talking about to educate me and calm me down.

---

### Post by macogw on 2007-12-19
Gutsy Gibbon works fine with NTFS, and there's a driver for Windows to be able to access ext2 and ext3 Linux partitions available from [http://fs-driver.org](http://fs-driver.org) :)

As far as partitioning, you can't install much in 6GB, but that's enough to play with a bit.  Defragment Windows before you try to resize it (which happens during Ubuntu's install--there's an automatic dual-boot option), though.

---

### Post by LaRoza on 2007-12-19
A few facts:

* Setting up a dual boot is easy with Ubuntu
* Ubuntu can now read and write to NTFS with no problems

To simplify the process, boot the live disk (after burning it as an ISO) and have it automatically resize and install as a dual boot.

It is best to defrag Windows first, and back up your system. If you don't have recovery disks, make them. The option is almost always there.

[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

You can resize the Windows partition with  a simple slider, don't move it too far to the left, as that will shrink the Windows partition a lot.

If you are really worried, play around with the Live disk or install VirtualBox in Windows (if you have the RAM, 1 GB)

---

### Post by anewguy on 2007-12-19
I'd follow the above to install Ubuntu in a dual-boot mode.  Just remember when going through to follow as they say and resize your existing partition to make room for Ubuntu (all part of the installation process itself).  As mentioned, defrag your windows partition first, then also check to see how much disk space is used - this should give you an idea of the maximum space you'll be able to allocate to Ubuntu.

As far as your wireless goes, if it's something like a Broadcom 4318, we can get that working even with a few simple steps with ndiswrapper.  Some people seem to have trouble with the new restricted driver for it but I don't know why - I just know I've gotten it to work with ndiswrapper many times.

So, go ahead and take the plunge!  Once you have Ubuntu installed, post back here so we can walk you through identifying your wireless card and the steps needed to make it work.:)

---

