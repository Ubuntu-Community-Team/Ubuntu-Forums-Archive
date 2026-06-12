---
title: "Dual Booting on Mac Mini G4 help"
date: 2006-11-14
forum: Apple PPC Users
---

### Post by zachtib on 2006-11-14
I have the first generation Mac Mini G4 (1.25GHz, 256mb, Radeon 9200 32mb)

After a number of requests for a PPC version of Deluge, I've decided to start working on officially supporting it, including PPC debs in the Deluge repository.

Now, I need to do one of a few things.

My first idea was a LiveCD.  I have reconstructor installed on my x86 laptop, can I use reconstructor on a PPC cd from an x86 laptop?  Basically, I need to rebuild a Dapper 6.06.1 CD and add in build-essential and svn.  Just enough for me to grab the source code, compile, and build the deb file.

What I'd like to do is set up a Dual Boot.  My Mini only has a 40GB drive, and its pretty full, but I have an external 250GB USB drive as well.  Could I install Ubuntu onto a partition of that drive, then plug it in and boot to it occasionally?  This is my preferred method.

The final solution would be to set up a dual boot on the Mini's internal hard drive.  I can move some files off onto the external drive that I mentioned earlier and then partition off a few GB from the end of the drive.  What's the lowest amount of space I could get away with in this situation?  I'd like to keep it at around 5GB, if that will be enough to house Dapper + build-essential + subversion, and then a number of libraries that are needed to build.  If someone can link me to a howto for dual booting OS X and Ubuntu, I'd appreciate it.

In no way do I want to cut myself off from my OS X installation.  As a CECS major, I want to have access to all platforms in order to make my software as portable as possible, and that means porting to other operating systems as well.

Thanks for your help

---

### Post by stmiller on 2006-11-15
Okay- yes ubuntu can install onto an external drive. You simply make sure it is plugged in, and choose it as the target at the ubuntu installer. The difficulty in PPC hardware is that now you must somehow tell your mini internal hard disc to look to the firewire drive to boot from that partition. You can write yaboot into the mac mini's boot partition, and have a custom yaboot.conf. (This can be removed and restored back to the original OS X partition, if you are worried).

My friend did this with his iBook. Has debian on an external drive. Internal drive is untouched. So it can work.

A 6GB partition should be plenty.

-------------

To set up a dual boot, simply put in the OS X install DVD, and at the beginning when it boots into the installer, choose the disc utility from the top menu bar. Make 2 partitions. You can place OS X in either one. I have OS X in the later partition for my system. It doesn't matter. Then install as normal.

Now pop in the ubuntu PPC disc, and install ubuntu, pointing it to the free/other partition on the drive. It will install, and not bother the OS X partition. 

You have to then edit yaboot.conf, and write the yaboot changes to the partition ($ ybin -v) so you can be able to boot into either OS X or Linux at boot.

---

### Post by NerdHerd628 on 2007-11-22
I cannot find my Tiger DVD.  Is it poosible to set up a dual boot without it?

---

### Post by BladeMelbourne on 2007-11-23
I currently get my deluge-torrent debs from [http://packages.debian.org/](http://packages.debian.org/)

Azureus was too taxing on my Mini's CPU/RAM usage. Deluge is lighter, faster and supports PG block lists - great torrent client :-)

---

### Post by oswaldkelso on 2007-11-24
> **NerdHerd628 said:**
> I cannot find my Tiger DVD.  Is it poosible to set up a dual boot without it?

Yes

see  [http://www.my2bits.org/?p=81](http://www.my2bits.org/?p=81)

---

