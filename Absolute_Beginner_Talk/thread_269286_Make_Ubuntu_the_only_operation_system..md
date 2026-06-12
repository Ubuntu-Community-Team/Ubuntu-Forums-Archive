---
title: "Make Ubuntu the only operation system."
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by firebirdworks on 2006-10-01
My laptop is pretty messed up.  And my usual linux is completely offline for good.  So I need to revert back to the laptop.  Unfortuately, the laptop sucks.  Is there a way to completely format the C drive without a xp startup disk?  I need to run linux live cd, but it the C: is to clogged up with viruses and such.

---

### Post by bulldog on 2006-10-01
Just boot from the live cd and when you install and get to the partitioning,let gparted use the whole drive option and it should be allright.

It will reformat your hdd and install Ubuntu on it.

---

### Post by crokett on 2006-10-01
What does running the live CD have to do with the C drive? The live CD is there for situations where your HDD is fragged.  Boot the Ubuntu live CD, run gparted and delete all the partitions on the drive.

---

### Post by wpshooter on 2006-10-01
Yes get KILLDISK from this site and WIPE the hard drive clean.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck.

---

### Post by firebirdworks on 2006-10-01
Yeah, but the laptop is so bad that there isn't enough remaining C drive space to run ubuntu.  I need to reformat it before the live cd can even think about running.

---

### Post by firebirdworks on 2006-10-01
Thanks, that killdisk thing looks good.

---

### Post by bulldog on 2006-10-01
You have to boot from the live cd not from your windows!!

And your live cd takes care of the all the bad things on your c:\

Have no worry's about that.:D

---

### Post by wpshooter on 2006-10-01
> **bulldog said:**
> You have to boot from the live cd not from your windows!!

And your live cd takes care of the all the bad things on your c:\

Have no worry's about that.:D

I don't think that is **always** absolutely true (although it should be).  I have had occasions where only WIPING the drive with a good third party utility would allow the Ubuntu installation to proceed properly.

---

### Post by firebirdworks on 2006-10-01
Ok, next little problem.
I need to make the kill disk into a live cd.  But I need to add it as a immage, not a file.  Any help with this?

Oh, and thanks for the help so far.

---

### Post by bulldog on 2006-10-01
> **wpshooter said:**
> I don't think that is **always** absolutely true (although it should be).  I have had occasions where only WIPING the drive with a good third party utility would allow the Ubuntu installation to proceed properly.

That could be possible yes,but I don't want to confuse TS to much and try the simple things first :D 

If this fails we can always provide other options however.

But thank you for this info.

---

### Post by bulldog on 2006-10-01
> **firebirdworks said:**
> Ok, next little problem.
I need to make the kill disk into a live cd.  But I need to add it as a immage, not a file.  Any help with this?

Oh, and thanks for the help so far.


No need for that,just boot from the live cd........................:)

---

### Post by firebirdworks on 2006-10-01
I can't, the live cd requires some amount of memory and speed.  Both of which my computer lacks, majorly.  I need to clear the c: drive before the live cd will run.

---

### Post by Imsati on 2006-10-01
Well, this one's a bit old-school, but it works great for older systems (hell, newer ones too, but it teakes longer), and those with really messed up hard drives...

Say what you will about WinME, it had a great start-up disk option. Just load it up, don't allow CD support, run Fdisk from the A: prompt and it walks you through it. Reboot after, enable CD support, format C: and load up Ubuntu!

After the Live CD is loaded, Format again using Ubuntu.

Takes a bit, but super-simple.

---

### Post by Imsati on 2006-10-01
Sorry--link to making an ME boot disk

EDIT: Sorry again--listed the wrong site.  This one works!

[http://bootdisk.com/](http://bootdisk.com/)

---

### Post by wpshooter on 2006-10-01
> **firebirdworks said:**
> I can't, the live cd requires some amount of memory and speed.  Both of which my computer lacks, majorly.  I need to clear the c: drive before the live cd will run.

Do you have a floppy drive on your machine ?

If so, download the floppy version of KILLDISK.

I assume you have another working machine !!!

---

### Post by bulldog on 2006-10-01
> **firebirdworks said:**
> I can't, the live cd requires some amount of memory and speed.  Both of which my computer lacks, majorly.  I need to clear the c: drive before the live cd will run.

Can't see the correlation.....](*,) 

You boot the live cd from the BIOS **NOT** from windows.

So windows will not be loaded and you have nothing to do with your hdd and all the RAM is available to you.

I'm getting too old for this stuff.](*,) 

Good Luck anyway.

---

### Post by firebirdworks on 2006-10-01
Alright!
Thanks alot for all the help.  I have a linux again!

---

### Post by Imsati on 2006-10-01
> **bulldog said:**
> I'm getting too old for this stuff.](*,) 

You have a great sig though!

Locutus was much cooler than Annika.


firebird,

Do you know how to boot a CD from BIOS? On most, you can enter setup and change the order of the boot devices. Move floppy or CD to 1 or 2 and Hard drive to 3.

On some, you can access a boot menu and select without going through the setup screen.

---

### Post by steve.horsley on 2006-10-01
firebirdworks:
The live CD doesn't touch the hard disk (until you tell it to install to hard disk). If the live CD won't run now, then it still won't run after you clear the hard drive. In that case, you will be wanting the "alternate" installer which runs in text mode rather than a memory hungry GUI.

Whichever installer you use, choosing to use the entire hard drive for Ubuntu will then delete the existing partitions , losing any viruses that were on them.

---

### Post by firebirdworks on 2006-10-01
Yeah, your right.  But whipeing my C: definately helped.  Thanks for everything, it runs good now.

---

### Post by crokett on 2006-10-01
> **firebirdworks said:**
> Yeah, but the laptop is so bad that there isn't enough remaining C drive space to run ubuntu.  I need to reformat it before the live cd can even think about running.

I see you got your problem solved but still don't see the connection.  The live CD has nothing to do with your hard drive and would boot whether or not you have a HDD installed or not. Even if your HDD is stuffed to the gills, the live CD should still boot.

---

