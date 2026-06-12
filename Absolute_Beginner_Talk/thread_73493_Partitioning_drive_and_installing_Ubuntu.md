---
title: "Partitioning drive and installing Ubuntu"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by AndyC_772 on 2005-10-09
Having played with Ubuntu on my desktop PC for the last few weeks, I'd like to set up my laptop to dual boot as well.

My laptop currently has a 40GB disc which is nearly full. So, what I'd like to do is upgrade to an 80GB disc, and partition it 40/40 for XP and Ubuntu. I can then copy the original disc to one of the partitions, leaving the other 40GB for Ubuntu. If I get an external Firewire caddy, that can accommodate one of the drives during the copy process. Alternatively I'd need two 2.5-3.5" adapters to plug them both into my desktop.

Can anyone please recommend a tool that can copy/partition the drives in this way? I presume Partition Magic could do it, but that's rather expensive and probably overkill. Is there a cheaper or free alternative?

---

### Post by Hobbsee on 2005-10-09
not sure how much you would need to backup of your windows, seeing as most of your programs wont work unless you copy the registry as well.  And no, I have absolutely no idea how you would go about doing that.  As for all your documents and configuration settings, i'd suggest burning it to a CD.  I dont know how Firewire caddy works, but you could probably use that as well if you were to copy files to there, and copy the rest back.

As for partitioning drives, the ubuntu installer will do it :)  [https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo) for more details.  If you can, make your windows partition 40 gig to start with, with the XP installer.  Otherwise just resize the partition (after defragging it!) during the ubuntu install.

---

### Post by AndyC_772 on 2005-10-09
It's the copying of my Windows partition that's the tricky part - I know how to partition the new disc. It's a doddle to copy data files across (just copy to CD, an external HD or a network server and back again), but I'd prefer to make an exact clone of the partition so I don't have to reinstall Windows, all my drivers and software.

---

### Post by mlomker on 2005-10-09
You can use [sysresccd]("http://www.sysresccd.org/"), which includes partimage.  The CD is based on a 2.4 kernel, which doesn't boot on every machine.  I like it because it is designed for disaster recovery and has drivers for almost every filesystem/disk type/network card that you could imagine.

Partimage is also on [Knoppix]("http://www.knoppix.net/get.php").

---

### Post by AndyC_772 on 2005-10-09
Sounds ideal - thanks!

Don't suppose you know whether or not it supports a hd connected by Firewire?

---

### Post by mlomker on 2005-10-09
> Don't suppose you know whether or not it supports a hd connected by Firewire?

Knoppix has a 2.6 kernel, so I imagine that's a better bet.

---

