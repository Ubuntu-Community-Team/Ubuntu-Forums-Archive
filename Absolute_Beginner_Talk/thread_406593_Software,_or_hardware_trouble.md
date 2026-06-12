---
title: "Software, or hardware trouble?"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by geoff_561 on 2007-04-11
I'm having trouble with burning CD's.  It appears that, converting MP3's to Audio CD format goes fine, for Gnomebaker, and Serpentine.  As far as burning goes, that's a big no, it fails.  That's using CDR-W disks.  I've used two different brands of CDR-W types, with the same result.  

However, with just CDR's, I have the constant problem, of the drive, spitting the disk back out at me.  Meaning, I close the drive, with the disk, it'll sit tight for about 30 seconds, then automatically eject.  Again, two different brands of disks, same result.  

Now, I'm coming to the conclusion, that it's my burner, however, it says that my burner is supported by Linux.  The burner is Easy CDWriter CR-4804TE.  

Now, I used this same burner, with the same types of discs on Micro Windows, and an unsure, if maybe it's a thing with Linux.  Or if their's some kind of install, I can use in order to fix this problem?  Or if it's a hardware problem?

I'm at a loss as to what it could be, and come to the great sages of Ubuntu for assistance.  

Thanks,
Geoff.

---

### Post by cantormath on 2007-04-11
> **geoff_561 said:**
> I'm having trouble with burning CD's.  It appears that, converting MP3's to Audio CD format goes fine, for Gnomebaker, and Serpentine.  As far as burning goes, that's a big no, it fails.  That's using CDR-W disks.  I've used two different brands of CDR-W types, with the same result.  

However, with just CDR's, I have the constant problem, of the drive, spitting the disk back out at me.  Meaning, I close the drive, with the disk, it'll sit tight for about 30 seconds, then automatically eject.  Again, two different brands of disks, same result.  

Now, I'm coming to the conclusion, that it's my burner, however, it says that my burner is supported by Linux.  The burner is Easy CDWriter CR-4804TE.  

Now, I used this same burner, with the same types of discs on Micro Windows, and an unsure, if maybe it's a thing with Linux.  Or if their's some kind of install, I can use in order to fix this problem?  Or if it's a hardware problem?

I'm at a loss as to what it could be, and come to the great sages of Ubuntu for assistance.  

Thanks,
Geoff.

I think it is permissions.
I had a similar problem, what I did was either start the burning program as root (not a great idea) or open terminal and 

> ~$ sudo chown username /media/cdrom (or whatever your burners mount pt is)

not a definite solution, just a suggestion.  As far as the disk spitting, I haven't a clue.

---

