---
title: "cycling on loading second stage (8.04 on g5 powerpc)"
date: 2008-07-18
forum: Apple Hardware Users
---

### Post by dustbunny0 on 2008-07-18
I have a G5 powerpc ([http://en.wikipedia.org/wiki/Power_Mac_G5](http://en.wikipedia.org/wiki/Power_Mac_G5)).  I installed ubuntu using the iso named: ubuntu-8.04.1-desktop-powerpc.  I chose the option to let it automatically parition and use the entire disk.

After the install finishes and it tries to come up for the first time, I get:
----------------------

First Stage Ubuntu Bootstrap

Press l for GNU/Linux
      c for CDROM

Stage 1 Boot:
Loading second stage bootstrap....

----------------------------

It waits about a minute and cycles thru this screen repeatedly until I hold the power button and force it to stop.

I've seen a few suggestions in various places for similar sounding issues and have tried (haphazardly) applying a few of the suggestions (manually mounting /dev/sda3 as root and various frobbing of yaboot.conf and running ybin) but I don't have enough of a grasp to know if I'm doing it wrong or if my problem is different from the others I see. 

- I would greatly appreciate suggestions on how to troubleshoot and complete the install (and actually understand what is going on)
- AND/OR if any one has successfully gotten a recent flavor of ubuntu running on this beast I appreciate hearing the path you took so I can try alternate steps.

As an aside I was going to try reinstalling OS 10.3 again and maybe try doing a dual boot but the OS X installer doesn't see any disk at all (there are no targets available in the gui installer to install to - but that may just be because it is confused by seeing the ext3 partitions, etc)

thanks

db0

---

### Post by stream303 on 2008-07-18
I've got a feeling your PPC Powermac has a dual-controller for hds, which can confuse yaboot.  In this case, it seems the trick is to use an alias in the yaboot.conf file such as:

hd:3

Check out this thread, especially the part that gets down to using openfirmware aliases in the /etc/yaboot.conf file :

[http://ubuntuforums.org/showthread.php?t=833570](http://ubuntuforums.org/showthread.php?t=833570)

As for the OSX reinstall, it is failing because it needs to be partitioned again - your dedicated ubuntu install used the whole disk.  What you can do is just before actually going ahead with the install, is to go to the top panel, and bring up disk utility.  Use disk utility to create an apple partition, say for only half of the drive and leave the other part open as free-space.  Then finish up with the OSX install.  When that is done, you can install Ubuntu to the free space, and yaboot will find your existing osx install and offer it as a boot choice.

Of course, you'll still need to go in and fix the yaboot.conf file possibly with those aliases mentioned in that thread.

---

### Post by tiresia on 2008-07-18
I own a PowerPC g5 and I could install Ubuntu without problems (I used the LiveCD because with the alternate version fans were too loud...).
Anyway if you want to have a dual boot (I have too), you should erase your HD and install first OSX. I would suggest to make two partitions: the first unformatted for Ubuntu and the second one formatted with hfs+ for OSX. 
Do you know which kind of G5 you have? Mine is a 2x2.5GHz (2004)

---

### Post by stream303 on 2008-07-19
> **tiresia said:**
> I own a PowerPC g5 and I could install Ubuntu without problems (I used the LiveCD because with the alternate version fans were too loud...).

Allright!  Another successful G5 powermac up and running..  I think what may have made it easier for you is that your model officially supports two hard drives, but uses a single hd controller, unlike dustbunny's powermac.

Interesting to hear that the live-cd had the fans under control during install.  For anyone doing an install with the "alternate" image on a G5, the fans will scream during install, but will calm down at the first reboot.  I've been told that this issue has been fixed in 8.04.1, but haven't verified it yet.

---

### Post by dustbunny0 on 2008-07-19
thanks stream303, that was exactly the tip I needed.  now i'm up and running (after a frustrating week).

db0

---

