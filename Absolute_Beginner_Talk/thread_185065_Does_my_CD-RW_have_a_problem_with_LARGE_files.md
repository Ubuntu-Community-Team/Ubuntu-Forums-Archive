---
title: "Does my CD-RW have a problem with LARGE files?"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by H.E. Pennypacker on 2006-05-31
I don't know what it is, but I can't burn ISOs the size of Distro Live CDs, although I can burn, say, GParted very well.  I believe the drive can also burn music and whatever, but none of that matters.  It will never succeed with Distro Live CDs, and what's in common is the large size of those files.  

Is my CD-RW drive like an old man who can't complete a walk through the park?  Keep in mind I bought this laptop December 2005.  It's brand new.

It's Philips SCB5265 with the latest firmware (17).  I tried installing ASPI layers with forceASPI to see if that worked, although I use Win. XP SPII.

**MDSums check out.  Everything's fine, except the burn part.**

---

### Post by Jucato on 2006-05-31
What problems are you encountering when you burning Live CD ISO's?
Also check your CD's if they're capable of holding that capacity. Most ISO sizes are 650-700MB, AFAIK.
Also make sure that you are burning ISO as an image, and not as a Data CD (but I guess you know that already, based on your successful experience with Gparted?)

---

### Post by Bartender on 2006-05-31
Do you mean the drive will start the burn, then just quit, or it won't even start the process if it's a large job?

---

### Post by H.E. Pennypacker on 2006-05-31
**Fenyx**, I've tried a whole bunch of different applications, and all give me a different error, so I can't really specify an error, or tell you what the real problem is.

The CD-RWs I use can and should be able to handle the load..after all, they say 700MB.  I am burning the ISOs as images.

**Bartender**, they will start, and stop, as you said.  Alcohol 120% is able to go the farthest reaching 50%, while others fail at almost exactly 13%.

I've done Google searches with all my errors, but nothing useful shows up.

---

### Post by H.E. Pennypacker on 2006-05-31
What's even more bizarre is that MD5Sums do check out, but the burns always go wrong.

---

### Post by arsenic23 on 2006-05-31
What error does Alcohol give you?
Have you tried Nero?  What error does it give you?

If you could post your logs from those two problems I could more then likley give you a pretty educated guess as to the source of your problem.

---

### Post by H.E. Pennypacker on 2006-05-31
Alcohol 120% provides the following error (I removed all the unnecessary info about the software, and computer info - too long in length).

********* Time stamp of this log file:  5/30/2006 10:45:00 PM *********
22:45:00 Processor info: Pentium M processor (1396MHz)
22:45:00 Memory Available to Windows: 253,308 KB
22:45:00 Not enough Memory! Adjust memory buffer size to 51 MB.
22:45:00 Image file loading: C:\Program Files\Files\RPMS\ubuntu-5.10-live-i386.iso
22:45:00 Source Info:  Session: 1, Track: 1, Length: 627.5 MB / 071:23:52
22:45:02 (D:) PHILIPS CDRW/DVD SCB5265(0:1): Recording Method/Speed
22:45:02 Recording - DAO / SAO - 4X (600 KB/Sec)
22:45:02 (D:) PHILIPS CDRW/DVD SCB5265(0:1): BURN-Free activated
22:53:55 (D:) PHILIPS CDRW/DVD SCB5265(0:1) - [Write ERROR], LBA: 147632, Length: 16
    S:KEY - 03/0C/00  - "Write Error"
22:53:56 (D:) PHILIPS CDRW/DVD SCB5265(0:1): Recording failed!
22:53:56 Error message:  [03/0C/00] - Write Error
22:53:56 (D:) PHILIPS CDRW/DVD SCB5265(0:1): Recording failed!
22:53:56 Image file loading aborted!
22:53:59 Something is wrong with the recording procedure! Please check the log file and report any errors to Technical Support.

I have tried Nero, but I can't remember the error.  I'll try it again.

---

### Post by arsenic23 on 2006-05-31
Laptop right?
I'm assuming your doing this while plugged into the wall and not on battery.  So, hmmm, what kind of background processes are running on your machine?  Do you have Norton (anything) on your machine?  Because I could see that possibly being the problem, but your right, that is a rather vague error log.

The first thing I'd try is this:  Kill all the background processes you can, and then force the burn process at 2x.  Though if you don't have something like Norton running, this more then likely won't help.

---

### Post by H.E. Pennypacker on 2006-06-06
It turns out the problem was with the CD-RW CDs I was using.  I tried to get things working on four different drives and three different computers, and those CDs wouldn't work.  I went to the store and purposely bought a CD (in this case, CD-R, because the store didn't have any CD-RWs) from a different brand.  

Thanks to all.

---

