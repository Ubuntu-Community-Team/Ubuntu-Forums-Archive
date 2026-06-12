---
title: "Need help with GIMP display problems"
date: 2013-05-21
forum: Art &amp; Design
---

### Post by Derelinquat fenestras on 2013-05-21
Hello,

I am a photographer and use GIMP quite extensively.  I am running it on an Acer Aspire One with a 10.5" display.  I'm running Ubuntu 13.04 with GIMP 2.8.  Up until a few months ago, I had no issues, but now the bottom end of my GIMP is cut off which makes operation of certain feature of GIMP impossible.  I've tried to [ALT]-click and drag windows so that I can see the bottom and click the okay option, but it will not drag up.

Does anyone else have this problem and does anyone have any idea as to how to fix it?

---

### Post by sudodus on 2013-05-21
It is a good idea to stick to LTS versions for production systems. Then you will have a stable system that will simply work in most situations. Are you running gimp from the repos or a bleeding edge version directly via some ppa? And do you need 2.8?

So I suggest that you run Ubuntu 12.04 LTS (again?). It may be easiest the download the point version 12.04.2, so that you need not update and upgrade too much.

---

### Post by Derelinquat fenestras on 2013-05-21
Thank you for your reply!

Do you know if there is a way to revert back to 12.04?  or will I have to back up and make/run a boot disk installation?

---

### Post by sudodus on 2013-05-21
No there is no automatic way back (only forward). You need to back up anyway, to keep your picture files safe ;-)

Many people have one production system (LTS) and a testing system where a new OS and new application programs and versions are tested. I am one of them. And I wait for at least 3-4 months after a new LTS version is out until I upgrade my production system. The LTS versions are released in April even years ... 8.04, 10.04, 12.04, 14.04 ... and I wait at least until August when the first point release it out (for example 12.04.1).

Next time, make a complete backup (image) of your drive just before you start upgrading. If you are not happy after the upgrade, you can restore the previous system from the backup.

---

### Post by Derelinquat fenestras on 2013-05-21
Thank you for all of the info...

This may seem like a ignorant question, but what is the difference in the point releases?

---

### Post by sudodus on 2013-05-21
All the upgrades (of the packages included in the release) are included in a new iso file. (It sort of corresponds to the service packs SP1, SP2, SP3 for Windows). So when you download the newest point release, you need not do a lot of time-consuming updating and upgrading from the original release of the version. Ubuntu makes point releases only of the LTS versions.

These upgrades are security upgrades as well as bug-fixes and other improvements of the program packages.

---

### Post by Derelinquat fenestras on 2013-05-21
Thank you!

I have on more question regarding GIMP.  I got GIMP 3.8 about a year ago, but I had to use extra PPAs to get it because only 3.6 was provided by Ubuntu.  I believe that I read that 3.8 comes standard with Ubuntu now.  Do you think I should ppapurge the repositories I used to get 3.8 and reinstall?

---

### Post by sudodus on 2013-05-21
Yes it is definitely worth trying :-)

In Ubuntu 13.04 it is probable that the GIMP from the Ubuntu repositories works better than the one from the PPA. But in 12.04 LTS you need the GIMP from the PPA if you want version 2.8.

---

