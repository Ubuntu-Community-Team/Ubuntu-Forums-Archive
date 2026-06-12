---
title: "Mac powerpc g4 install hangs detecting hardware"
date: 2009-07-17
forum: Apple Hardware Users
---

### Post by williwinki on 2009-07-17
Hi.  I'm a Linux novice and have decided to install Ubuntu.  I have a little experience with AIX so Unix type OS's aren't totally foreign to me. I had a long career in IT but now retired, so I'm not a novice to operating systems and computing in general.

I bought an old Mac powerpc, G4, Quicksilver, 867MHz, 1GB ram, integrated NIC card, 2 hard drives, Seagate Barracuda and Quantum Fireball, NVIDIA GeForce video card, everything old but functional. The computer cost me all of 10 bucks so thought I'd play around with Linux.  I have OS X 10.2.8 running on it and there don't seem to be any hardware issues.

Downloaded both the standard powerpc ISO and the alternate powerpc ISO & burned them both to CDs.

Tried all boot variations of both, ie those listed when using tab and suggestions in the boot text.

Standard ISO hangs at "Loading, please wait" no matter what boot options I use.

Alternate ISO hangs at "Detecting network hardware" no matter what boot options I use.

Tried skipping network hardware detection to see if HDDs would be found but same issue, just hangs there.

No error messages are issued.  I haven't been able to find a way to break out of the "Detecting hardware" without rebooting.  I assume there is a log (probably in ramdisk) but have no idea how to look at it even if I could break out of the detecting hardware but keep the install running.

Ran Mac diagnostics and all hardware passes with no errors, though diagnostics don't test CD or HDDs.

When using OS X there don't seem to be any issues with the HDDs or the CD.

I'm too hardheaded to give up.  I've seen notes from others saying they have Ubuntu running on the powerpc though not sure I've seen anyone who has installed 9.04 from scratch on one.

Anyone have any ideas where to go from here?  Any help would be much appreciated.

---

### Post by williwinki on 2009-07-17
Correction:  Not an integrated video card, it's an integrated NIC.  Video card I believe is a NVIDIA GeForce2.

---

### Post by crayZsaaron on 2009-08-16
Are you positive that you're waiting long enough for it to load?  I always get to the "loading, please wait..." spot, and it takes 5-10ish minutes to load.  Then it starts checking a bunch of things, and when it's done, I get a completely blank black screen, and after a few minutes I hear some noises... the first noise sounds like african drums and the second is similar but more music-like.  Then...nothing.:(

---

### Post by howlingmadhowie on 2009-08-16
i'm afraid i haven't got my G4 with me atm, but i remember the newer ubuntu ppc versions having real problems. the easy way would be to try a distro specially designed for ppc, like yellow dog.  the debian port also probably receives more love than the ubuntu version (which isn't officially supported anymore). if i remember correctly, i first installed 8.04 and updated from there.

have you looked here for tips? [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by LewRockwell on 2009-08-16
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

honestly, the LiveCD took forever to boot up on our G4 with 1.5ghz and 1.5gb ram

it seemed to get really hot fairly quickly and we didn't get the wireless working before I shut it down due to over-heating concerns

it would be great to have ubuntu running well on the older Mac stuff with PPC(IBM) processors but we're not holding our breath

.

---

### Post by Frak on 2009-08-16
I'd really say either find an old copy of 10.4 or install YellowDog. Ubuntu has given me more issues than any other PPC distribution, unfortunately.

---

### Post by Old_Grey_Wolf on 2009-08-16
I had a PPC G4 MAC that I got rid of a year or two ago after trying to salvage it for my grandchildren. It had OS 9. I installed Ubuntu PPC on it; however, I couldn't find a descent Flash Player for the PPC chip. Youtube didn't work correctly for example. Maybe someone has developed a Flash Player for the PPC running Linux since then. My grandchildren wouldn't have used it if the Flash games, etc. wouldn't work. You could try out several distors; however, I don't know if any of them still have Live CDs.

---

### Post by Frak on 2009-08-16
> **Old_Gray_Wolf said:**
> I had a PPC G4 MAC that I got rid of a year or two ago after trying to salvage it for my grandchildren. It had OS 9. I installed Ubuntu PPC on it; however, I couldn't find a descent Flash Player for the PPC chip. Youtube didn't work correctly for example. Maybe someone has developed a Flash Player for the PPC running Linux since then. My grandchildren wouldn't have used it if the Flash games, etc. wouldn't work. You could try out several distors; however, I don't know if any of them still have Live CDs.
What I'm wondering is why nobody has developed an alternative to watching youtube videos that loads mplayer, et al. instead.

---

### Post by williwinki on 2009-08-16
Folks, I started this thread and gave up on Ubuntu 9.4(Jaunty) altogether.  Spent many hours trying to get it to work on both Mac PPC and on a standard x86 PC.  I haven't heard of anyone who has it up on a Mac Quicksilver.  

Ubuntu wouldn't run the network cards on either platform, one wired one wireless.  Tried everything I could find on and off the forums.

Not sure if I'll try a different version of Linix.  Right now I'm pretty burned out on it.

Willi.....

---

### Post by marshag63 on 2009-08-17
I know how you feel - I had some problems installing on my G4 iMac, but it is happily running 8.10, with wifi.  

Try clearing pram (I do it at least three times) before letting the CD try to boot.  8.10 has a CD-rom driver problem - you need to modprobe the cdrom driver before you can install - there's a post somewhere about it.

I recall having an xserver problem and had to tweak mine - would be glad to share if you have problems. 

As for wifi, a Belkin F5D7050 USB adapter (version 3 or 4?) works with the zdw122 (need to verify that) module.

Also, be sure you change your repos to [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)

Flash does not work for PPC, but if you use firefox, download the add-on called Video Downloadhelper and you can download videos to watch (not as fun as flash, but it works).

If you try again, let us know how it goes.

MarshaG63

---

### Post by NathanLT on 2009-08-18
The Debian team provide an excellent PPC version of their distribution. The installer is text-based rather than graphical (even on Lenny, their most recent release), but don't let that put you off - installation (on my iBook G4 at least) proved painless and the distro ran as solidly as a rock. Wired networking worked out of the box, though wireless may prove problematic (in the end I gave up on my Apple AirForce One wireless card and bought a Ralink usb one, a couple of clicks to install the firmware and I was away!).

As marshag63 pointed out, there is currently no working version of flash available for PPC computers - Adobe refuse point blank to provide a version of their Flash Player for an architecture which they see as obsolete, and the open source alternatives (Gnash etc) don't work properly yet on any architecture.

Nathan

---

### Post by williwinki on 2009-08-18
Thanks Marsh & Nathan.  Ubuntu 9.04 was my first venture into the Linux arena.  Tried it on both a Mac G4 Quicksilver(wired nic) and a x386 PC(wireless nic).  Couldn't get either to work.  Spent several weeks and finally gave up.  I have many years of experience with computers and systems and don't very often get stumped.  But this one wore me out.

Just recently read a thread that noted 9.04 was released knowing that there were networking problems.  Well without networking a computer is worthless to me.  

And I don't want to use a back release knowing that future releases digress in their capabilities.  Maybe in a few weeks the sour taste in my mouth will go away and I'll try another flavor of Linux.  But probably not Ubuntu.

Thanks again for your input.

    Willi....

---

### Post by marshag63 on 2009-08-19
Perhaps Debian would work better:  I found this link to a live-CD (not PPC) (you can choose Gnome, KDE, XFCE or LDXE desktops).

[http://cdimage.debian.org/debian-cd/current-live/i386/usb-hdd/](http://cdimage.debian.org/debian-cd/current-live/i386/usb-hdd/)

You can install Debian on a PPC as well (just not from a live CD, as far as I can tell).

Hope this helps  :)

MarshaG.

---

