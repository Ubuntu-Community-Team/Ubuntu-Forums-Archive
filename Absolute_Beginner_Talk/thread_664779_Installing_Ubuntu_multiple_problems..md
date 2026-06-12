---
title: "Installing Ubuntu multiple problems."
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by MattTait on 2008-01-11
I got Ubuntu 7.10 32bit from the website, and succesfully burnt it to a CD.

When restarting, all of the options caused the computer to go to a text-mode kernel with no options to go to the Ubuntu desktop or install.

Eventually I found out that the problem was that my computer had an AMD64 processor, and I needed to enter the parameters:

irqpoll pci=noacpi noapic nolapic acpi=off.

When launching now, the usual linux text appears, but then fails with a kernel panic:

kernel panic: VFS: Unable to mount fs on unknown block(104, 1).

What do I do now?

No offense guys, I want to like and learn about Ubuntu, I really do. You all say how much better it is than Windows, but seriously, installing should not be this involved.

---

### Post by oldos2er on 2008-01-11
Can you post your hardware specs?

---

### Post by MattTait on 2008-01-11
AMD Turion 64 X2 Mobile Technology TL-52 1.61 GHz Processor
1023 MB RAM
NVIDIA GeForce Go 7600 Graphics card

And about 7 TB of hard disk.

---

### Post by oldos2er on 2008-01-11
Have you tried the alternate CD?

---

### Post by erniequintero on 2008-01-11
try this on the kernel parameters
 pci=assign-busses apicmaintimer idle=poll reboot=cold,hard

---

### Post by Crumpets and Jam on 2008-01-11
> **MattTait said:**
> I got Ubuntu 7.10 32bit from the website, and succesfully burnt it to a CD.

When restarting, all of the options caused the computer to go to a text-mode kernel with no options to go to the Ubuntu desktop or install.

Eventually I found out that the problem was that my computer had an AMD64 processor, and I needed to enter the parameters:

irqpoll pci=noacpi noapic nolapic acpi=off.

When launching now, the usual linux text appears, but then fails with a kernel panic:

kernel panic: VFS: Unable to mount fs on unknown block(104, 1).

What do I do now?

No offense guys, I want to like and learn about Ubuntu, I really do. You all say how much better it is than Windows, but seriously, installing should not be this involved.

Have you tried the 64 bit version of Ubuntu?

---

### Post by Bartender on 2008-01-11
> **MattTait said:**
> No offense guys, I want to like and learn about Ubuntu, I really do. You all say how much better it is than Windows, but seriously, installing should not be this involved.

It's frustrating not getting the desktop at the first try but there are a million things that could go wrong and many of those come back to operator error.

We don't know if the CD is good.  Common mistakes - 
Using cheap discs.
Using a CD-RW instead of CD-R.
Burning at a faster speed than your optical drive can handle.
Not verifying the download md5sum.

Can you toss that CD in another machine - Intel or AMD - and see if it takes you to the desktop?  If it won't boot, CD may be no good.  Try another PC.  If it fails on 3 different PC's then assume CD is no good.  Try again.  Use same download if md5sum checks out or start over from scratch.

---

### Post by HemiGTX on 2008-01-11
ok you have the 32bit version of ubuntu and you're running a 64bit AMD... get the 64Bit Ubuntu alternate cd and all should go perfectly

---

### Post by MattTait on 2008-01-11
@oldos2er: The alternate CD suffers the same problem

@erniequintero: Thanks, but that also doesn't work. Both my arguments and yours appear to generate the same error.

@Bartender: The CD is good quality, and a bincheck says that there's a 0% error between the CD and the ISO and the ISO matches the md5 on the site.

I've noticed that when booting with no arguments at all, it complains about the lack of a "root=" parameter in the command line.. any hints?

---

### Post by MattTait on 2008-01-20
Thanks all.

I finally figured out what the problem was.

The problem was that I had the wrong disk in the drive (duh). I was using Ubuntu, when I should have been using XP. I tried Linux a couple of years ago as well, and I was willing to try it again, but frankly if it can't even boot to the desktop after a week of trying, then I can't be bothered.

You know how they say you form an opinion of someone in the first 30 seconds of meeting them? It's the same for OSes. And Ubuntu sucks.

---

### Post by madjr on 2008-03-08
> **MattTait said:**
> Thanks all.

I finally figured out what the problem was.

The problem was that I had the wrong disk in the drive (duh). I was using Ubuntu, when I should have been using XP. I tried Linux a couple of years ago as well, and I was willing to try it again, but frankly if it can't even boot to the desktop after a week of trying, then I can't be bothered.

You know how they say you form an opinion of someone in the first 30 seconds of meeting them? It's the same for OSes. And Ubuntu sucks.

glad you think Ubuntu sucks and the community wasn't friendly enough....

---

### Post by NightwishFan on 2008-03-08
Fine. Go crawling back to Vista. Go tell Gates your mission has failed. You think he will let you live after such a disaster? Your computer will be ridden with spyware within the hour. Hahahaha.

---

