---
title: "can't make Xubuntu boot from CD on aged PC"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by andy hughes on 2007-12-08
Hello,

I've been given a Packard-Bell Club 60 PC which I would like to pass on to my parents so they can experience the internet at home rather than in the local library.  It came with Windows 98 installed but the v5 explorer didn't work properly (it kept identifying "runtime errors" in every webpage).  Since Windows 98 is now not supported, I thought it would make sense to migrate to a modern freeware operating system that would be secure and stable (and more flexible than Windows!).

The PC has a 6GB hard drive, Celeron 400 Mhz processor and 64Mb RAM, so a limited installation of Xubuntu looked just the thing.  I reformatted the hard drive, downloaded the latest Gutsy Gibbon .iso file onto my iMac and burnt it to CD at 8x speed (the slowest available).  The checksum for the CD file matches that on the Xubuntu download page, so it hasn't been corrupted.

I set the PC Amibios (CMOS) to boot first from CD, then put the CD in the drive and tried to boot the machine.  The CD drive light came on for a few seconds and it whirred a bit before stopping; a message on screen reported that there was no boot record on the cd-rom. :(  The machine then tried to boot from floppy and then the hard drive as per the CMOS settings.

If anybody has any suggestions as to what might be wrong I'd be very grateful.  Have I made a rookie error or is there something fundamentally wrong with the PC?  Whilst I have used unix, Macs and PCs in the past, I've never dabbled with installing new operating systems before.

Many thanks in advance,

Andy

---

### Post by laidback on 2007-12-08
Did you just burn the .iso onto the CD or use the .iso to create the bootable cd. You can check this by looking at the cd with your imac. If you have a single .iso file on the cd than you didn't burn it using the correct options. If on the other hand you can see loads of files and folders then you may assume at least the cd seems OK.

---

### Post by laidback on 2007-12-08
I have some old RAM lying around that you might find suitable for an upgrade to 128Mb or beyond. Email me via the forum if you like.

---

### Post by andy hughes on 2007-12-08
Thanks laidback, you were right: unfortunately, having written the unpackaged files and folders to to a dvd, the PC now says "invalid system disc" (it's drive is a DVD & CD reader, so the change in format shouldn't be a problem - the unpackaged files amounted to 1.4GB and so required a DVD).

---

### Post by andy hughes on 2007-12-09
Problem solved!  I'd done something wrong (not sure what) when burning the CD.

Many thanks.

---

### Post by DJiNN on 2007-12-09
> **andy hughes said:**
> Problem solved!  I'd done something wrong (not sure what) when burning the CD.

Many thanks.

Hi Andy, glad that you now have the problem solved, but just wanted to mention that you "May" not be able to install Xubuntu (From the Live CD version at least) on that machine. Anything less than 128mb will be hard going and it may be a better alternative to use the "Alternate" version (Which uses a text installer). It uses less resources whilst installing, but you should end up with the same Xubuntu.

If i were going to install a Linux OS on such a machine, i would probably either choose one of the smaller (But in every way functional) distros such as Puppy or DSL (There are many out there to choose from) or even something like "antiX" which is Debian (Ubuntu) based anyway.   

By all means give Xubuntu a try, and it may work well & be just what you're after, but if you find that it's slow, or doesn't perform as you would like, have a think about some of the lighter distros. They're also a lot quicker to install than Xubuntu because they're so light,.

If you get the chance to upgrade the memory, even to 128mb, that would make a lot of difference.  

Whatever you decide to do, i hope it goes well & you have fun. :)

Cheers........

DJiNN

---

