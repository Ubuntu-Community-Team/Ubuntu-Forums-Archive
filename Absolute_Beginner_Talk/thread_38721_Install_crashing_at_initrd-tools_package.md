---
title: "Install crashing at initrd-tools package"
date: 2005-06-01
forum: Absolute Beginner Talk
---

### Post by realale on 2005-06-01
All,

Am attempting to install 5.04 on an old Win98 box at the office so they will dual boot.  Processor is a Celeron, 384MB, with a 10GB hard drive.  Partitioned the Windows portion to 4.5GB (only 3GB total on hard drive prior to attempting Ubuntu install), let the Ubuntu partitioner automatically partition the remainder (which it did as a root and a swap).  On subsequent install attempts, I have reformatted and mounted the root in the same manner as the partitioner set it up the first time through.  Everything is working well, apparently, until two-thirds of the way through the installation of the base system.

The first install generated the following:

    (1) The deboot strap program exited with an error (return value 2).  Check /var/log/messages or see virtual console 3 for details.

    (2)  The base system installation into /target/ failed.  Check /var/log/messages or see virtual console 3 for details.

    (3)  An installation step failed.  You can try to run the failing item again from the menu or skip it and choose something else.  The faulty step is:  Install base system.
 
Three of the last four install attempts generated the same error message:

Error returned while trying to install initrd-tools package.

The next error screen says:

An installation step failed.  You can try to run the failing item again from the menu or skip it and choose something else.  The faulty step is:  Install the base system.

The other installation attempt simply froze at 79% installed and indicated it was "Installing the kernel"

Any assistance is appreciated.  I'll check back in later this evening, though I won't have the work machine in front of me until tomorrow morning.

Dave

---

### Post by realale on 2005-06-01
Next install attempt repeated the error reported in the first post.

Next returned to the original error, except now referencing return value 1.

Next reported another debootstrap error and added the following:

Couldn't retreive aptitude.  This may be due to a network problem or a bad CD, depending on your installation method.  If you are installing from CD-R or CD-RW burning the CD at lower speed may help.

I then ran the CD integrity test and my CD failed with the following message:

./pool/main/a/aptitude/aptitude_0.2.15.8-1ubuntu12_i386.deb file failed the MD5 checksum verification.  Your CD-ROM or this file may have been corrupted.


Needless to say, I'm burning new CDs now (the one I was installing from was ordered).  Hopefully there will be no problems tomorrow.  I'll post again to close the loop.

Dave

---

### Post by heltinde on 2005-06-02
Hello Dave

As I recall it, I was recommended to use minimum 10 GB for Ubuntu, so perhaps just have to little space.

---

### Post by kvidell on 2005-06-02
[QUOTE=heltinde]Hello Dave

As I recall it, I was recommended to use minimum 10 GB for Ubuntu, so perhaps just have to little space.[/QUOTE]
 I donno about that. I'm only using up 6 gigs of my 80 gig drive and I'm in no way stingy with packages, and have a lot of "crap" on the drive (files, music, a few movies for in-flight entertainment, phtography (raw images), etc).

4 should be okay. Base install plus a small amount of flexibility in data. Not much, mind you... He'll probably feel like he's running off of a LiveCD after a little while, but at least he'll get a feel for how apt works, etc.

A new CD does sound like it's needed though... obviously, the checksum failed.

Do update :)
- Kev

---

### Post by NewbieNik on 2005-06-02
Had exactly the same problem installing on a HP Netserver LHPro this morning.
used the install switch of

linux aic7xxx=no_reset noapic nolapic

and installed fine. Seemed to be the odler hardware that was causing the issue.
Are you installing on a 10Gb IDE or SCSI drive and if SSI what controller are you using?

If on rebbot you get a grub 15 error, set up your hard drive to have a /boot drive of lower than 500Mb!!

---

### Post by realale on 2005-06-02
Thanks to all for the suggestions.  The home-burned CD is not being recognized, so I'll just wait for the official one from Ubuntu to arrive.  The one that was crashing was from linuxcd.org.

In the interim, I may not be able to resist upgrading the hard drive.  This computer is a test for our small office.  If we like how Linux performed on this box we were going to migrate in full.  We'll keep the newest box as a dual-boot for Windows-only situations, but these golden oldies are going to be dedicated Linux.

Thanks again, and I will close the loop once I get a functioning installer CD.

Dave

---

