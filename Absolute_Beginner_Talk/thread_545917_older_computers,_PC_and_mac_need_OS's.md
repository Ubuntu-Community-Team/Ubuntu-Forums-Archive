---
title: "older computers, PC and mac need OS's"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by shill on 2007-09-08
1.  I have  an old G3 mac/apple:
-We have no browser or way to connect this computer to the internet.  Works fine.  OS 8.6
-Is there a version of Ubuntu that will work on this box?

2.  A  PC with an AMD 750 processor, will be putting in a new hard drive, crashed for the 3rd time in 5 years or so, was running Windows 98.  Kids downloaded something again and corrupted the hard disks.
-At one time I did try to install Ubuntu on this machine about a year ago before it recently crashed (from IE use by the way, firefox worked).  It did not recognize the ethernet card and would not connect to the internet.

Needless to say, looking for a way to get these computers operational.

---

### Post by philinux on 2007-09-08
Burn the ubuntu live cd iso and try it out you've nothing to lose.

---

### Post by southernman on 2007-09-08
> **philinux said:**
> Burn the ubuntu live cd iso and try it out you've nothing to lose.Nothing but time, energy, cd coaster, and wasted bandwidth if the machines don't have the ram to run the livecd.

shill, How much ram are in the boxes. Knowing the processor speed is far less important than amount of ram, in determining what OS to suggest.

---

### Post by Myglaren on 2007-09-08
I have a Duron 750 on a Gigabyte board with 75 Meg of RAM and a 13GB HD running Dapper (too idle to upgrade yet) and it goes just fine.  It is also still running a somewhat crippled version of XP pro (the 'special' edition) on a 40 Gig drive.  Dapper certainly leaves XP standing.  Dead simple install too.  Picked up all the hardware and was on the net straightaway synching the clocks with Ubuntu's and checking for newer packages than the ones on the disk, which were then installed instead.  I was seriously impressed, a doddle compared to so many other operating systems.

I'd use a disc from Shippit rather than a download as my experiences with burning ISO discs are not encouraging (failed miserably)  if you want to get your hands on them a bit quicker, most open source software vendors have them for a couple of quid ( I bought Edgy from Holland for about £3 including postage)  On the other hand the Fiesty discs only took 10 days.  Amazon have them too but not at what I would describe as sensible prices.

There do not appear to be any Mac discs on offer anymore from Shippit but perhaps from an OSS vendor, again?

---

### Post by Xoanan on 2007-09-08
Only 75 MB of RAM and you got the Dapper live CD to run?  Wow.  I couldn't even get that to work 128 MB of RAM.  That's why I chose Xubuntu.

---

### Post by Myglaren on 2007-09-08
Silly me - sorry 750 Meg.

---

### Post by psyke83 on 2007-09-08
Shill,

If you're interested in trying Ubuntu on your G3 Mac, make sure to download the alternative install cd if you have less than 128mb ram. The desktop/live installer really needs more than 128mb to boot properly.

Here's the one you want: [http://releases.ubuntu.com/6.06.1/ubuntu-6.06.1-alternate-powerpc.iso](http://releases.ubuntu.com/6.06.1/ubuntu-6.06.1-alternate-powerpc.iso)
Or, for Xubuntu: [http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/xubuntu-6.06.1-alternate-powerpc.iso](http://cdimage.ubuntu.com/xubuntu/releases/6.06.1/release.1/xubuntu-6.06.1-alternate-powerpc.iso)

---

### Post by Xoanan on 2007-09-08
> **Myglaren said:**
> Silly me - sorry 750 Meg.

Ah.  That make sense.  at the moment, I can only dream of having 750 MB. LOL

---

### Post by SoloSalsa on 2007-09-08
Dude, get rewritable discs, first thing.  Regardles of bad burns of Linux, I am sure there are other things that you will eventually dispose of.  Really, if you think about it, old discs make up more e-waste than ink cartridges, yet extremely few people recycle CDs/DVDs (which ARE recyclable, yet few people do so).  I wrote to a rewriteable disc thirty times in three months; well worth it for me...

About the computers:  for the Macintosh, try Yellow Dog.  Regardless of how much RAM you have, Ubuntu will be a disappointment.  Ubuntu was optimized for PPC G4 and up.  I think it *might* work, but it would be so slow...  Fortunately, there is a distribution of Linux made just for Power-based Macs: Yellow Dog Linux.  It has all of the drivers necessary for Apple hardware, and handles as well as Mac OS.  It takes six discs, and ten gigabytes of storage, though, so you may not be able to use it...  If you can, try it!

---

### Post by shill on 2007-09-09
>Here's the one you want: [http://releases.ubuntu.com/6.06.1/ub...te-powerpc.iso](http://releases.ubuntu.com/6.06.1/ub...te-powerpc.iso)

tried this as well, the G3 did not recognize the the disc, could not run it.  Hoped to fine a Linux version as an alternative to OS 8.6.  I do not have the original disc for this box, it cannot connect to the internet.

Short and Sweet of it – Apple G3 Os 8.6
Info from System profiler: Personal web sharing and multi homing is off, Appletalk on Appletalk zone not available, file sharing off, router not available.
Net mask, IP, Default gateway, domain, and server shows unavailable.

TCP/IP installed.

The clock cannot connect to sync either.

---

### Post by BobBlec on 2007-11-02
> **shill said:**
> 

1.  I have  an old G3 mac/apple:
-We have no browser or way to connect this computer to the internet.  Works fine.  OS 8.6
-Is there a version of Ubuntu that will work on this box?



shill,
  Sorry to come in late on the thread...

  What kind of a G3 Mac do you have? This is *very* inportant, because some G3 Macs will run ubuntu fairly decently, and others are a *major* PITA to get running!

  iMacs and above are "New World" machines, and they run decently (albeit slow) on ubuntu; iirc, 5.10 or 6.06 was the last version that ran on G3 Macs.

  Anything below an iMac (i.e., beige G3) is an "Old World" machine (check [http://en.wikipedia.org/wiki/Old_World_Mac](http://en.wikipedia.org/wiki/Old_World_Mac) for more info). They won't boot the LiveCD; you have to install it through something like BootX or another bootloader, which tends to get a bit tricky, and has been known to cause tearing of hair and gnashing of teeth.  ;-)

  I went through it with a beige G3, and I've never *quite* gotten it to work...

  Hope that helps!

  -BobBlec

P.S. I'm running 7.04 on a Compaq Presario 5310 at this very moment; runs great!  :-)

---

