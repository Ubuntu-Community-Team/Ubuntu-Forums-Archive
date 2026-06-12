---
title: "Awww crap..."
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Sanus Compleo on 2007-11-06
Okay, I got the live cd to work, but for some reason it won't start out like it normally should, but that isn't my problem.  My problem is, that for some reason, I cannot get my second hard drive to reformat.  Not even from my windows xp hard drive.  Here's my setup:
Hard drive 1, 40 gig with windows xp pro
Hard drive 2. Nice lil maxtor, with 80 gigs, and xp pro, that will not load, due to a new chipset, so I wanted to install ubuntu on it.  All looked well, and eventually, after alot of work, I got the live cd to work.  That's where I'm at now.  I tried installing it, and went through all the steps, and it stopped at step six, well after a good hour or so I checked on the files in the maxtor, and it did seem that it changed some stuff around, but did not erase any of the old data [40 gigs worth],  Well, I let it run for another good two hours, and nothing else happened.  Wtf?  At this point, I am confused, so I go back to windows xp, and try to reformat the hard drive from there.  Well, then it gave me a warning in french (wtf?) and then gave me a similar looking warning in english, telling me that something was using the hard drive, and I could not reformat it.  I went into task manager, and closed out all processes, cept the few that kept the computer working, and made sure that I didn't have a single window open that would show the contents of the hard drive.  Again, I vainly attempt to reformat the drive.  Poof, nothing happened.  What did I expect?  Sigh...  My previous experiences with Ubuntu, included some extreme work on a hard drive, so I feel that this may be no different, but I am hoping that this time, a mystery fluid will not creep into my system, and cover only my ubuntu hard drive, crashing it quite abruptly, with a fair bit of smoke.  What I need now, is the info on how to reformat the drive via the live cd, and no I cannot access gparted, because I do not have root privileges.  PLZ HELPZORZ!

---

### Post by Dr Small on 2007-11-06
On the livecd, you can not access gparted because you do not have sufficient privaleges ??? What in the world!

---

### Post by rudeboyskunk on 2007-11-06
Maybe try disconnecting the hard drive during your Ubuntu install and then reconnecting it afterwards, and see if you can format it once you've had Ubuntu set up?

---

### Post by Sanus Compleo on 2007-11-06
I'd try to do that, except the hard drive that i need to set it up to is the one giving me problems, unless you're talking about the original hard drive for the computer, but I'm not sure if it has to do with that one.  Thanks for the input though.



EDIT:  In the install, if I go through the manual input, would it work just as well if I just deleted the partition that I wanted to use and then set up a new partition on the hard ware?  Or would that just let the smoke out of the magic box?

---

### Post by studo77 on 2007-11-06
The partitioning also gave me worries in the beginning. The easiest way is to boot into your Windose, and us some program to delete the partition for Ubuntu. Then when installing you use the Free Space option. Easist for a newbie i think.

Otherwise, if the LiveCD gives you trouble, and you just want to install. Try the alternative. It is just as easy, even a few more clicks are required.

---

### Post by Sanus Compleo on 2007-11-06
I couldn't get the alt cd to work, but after trying the live cd again, it did boot to the live w/e.  As I've already stated, I couldn't reformat the hard drive from windows.

[http://i12.photobucket.com/albums/a205/ScizorsGuru/Screenshot-1.png](http://i12.photobucket.com/albums/a205/ScizorsGuru/Screenshot-1.png)

That is the screenshot of the partitions.  I so do not know what to do next...

---

### Post by Sanus Compleo on 2007-11-06
Update here, um... I tried using the gksudo nautilus command in the terminal, and as with all things associated with me, it did not work.  Instead it just told me about how it cannot do something or other with root...

sigh...  I'm wondering if it would be acceptable to go back and physically delete each file on the hard drive, and then try to reformat it.  Would this work?

---

### Post by Sanus Compleo on 2007-11-06
Okay...  Um...  Does anybody have any more advice before I unplug my windows hard drive, and DBAN my maxtor?   I'm looking to fully partition the thing btw.

---

### Post by justsomedude on 2007-11-06
If I understand correctly, you want to install Ubuntu on your 80 GB drive.

All you have to do is to boot into XP and delete the ntfs partition on your 80 GB drive.

Then boot the Live CD and install with the option 'use biggest free space` on sdb.

In order to have the choice to boot XP or Ubuntu on startup, you will need to change your BIOS to boot from sdb and then make a GRUB entry for XP.

If you prefer to manually format this drive I recommend the GParted Live CD, it works wonders...

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by Sanus Compleo on 2007-11-06
Actually, as I thought I had said, I cannot reformat from my windows hard drive.  ALSO, the 80 gig was from another comp so it's chipset is wai different, and will not boot.  I'll either try gparted, or dban, and am really hoping for an alternative.  Thx again.

---

### Post by Sanus Compleo on 2007-11-06
OH MY GOD WTF DID I DO?  Okay... okay... uh well I used that one thingy... the gparted or whatever, and I figured that I wanted to delete the partition on the maxtor.  THE WHOLE DAMN THING'S GONE!  It's not detecting that it is still plugged in, or ever was plugged in.  PLEASE HELP!

---

### Post by Sanus Compleo on 2007-11-06
Please help?  Pretty please?

---

