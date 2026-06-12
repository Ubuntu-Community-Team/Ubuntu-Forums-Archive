---
title: "How can I tell when I installed Ubuntu?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by psyopper on 2007-07-09
So it's been about three months since I installed Ubuntu, but I can't remember exactly when. I recall a random post on here at one point where someone told someone else they could check the date when the installed Linux by looking at something in /var/log (I think).

I now it's not "support" but it is "Absolute Beginner"...

Thanks!

---

### Post by moore.bryan on 2007-07-09
*i've looked all around for you and the short answer is "no" and the longer answer is "not if you've upgraded the system at all."  there MIGHT be something somewhere in one of the /var/log files, but it doesn't look good.*

---

### Post by UnixAnt on 2007-07-09
I suppose if you have never rotated any of the log files and not performed a distro upgrade since the initial installation, you could head /var/log/messages and check the date of the first entry and see if it tallies with when you *think* you installed it.

---

### Post by psyopper on 2007-07-09
Well, a text search through /var/log returned about 20 hits. Most of them were returning it for the Buld Date of 4 April (the build date for the Feisty release...).

A few of them from different sources (mostly X logs) also contained:

Current Operating System: Linux Ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686

15 April sounds reasonably reasonable... 

The specific logs that included this string included:
/var/log/Xorg.93.log
/var/log/Xorg93.log.old
/var/log/gdm/:20.log.3
/var/log/gdm/:20.log.4

But here's something that looks even more "accurate"
/var/log/bootstrap.log 

returned this:

Setting up tzdata (2007b-0ubuntu1) ...
Current default timezone: 'UTC'.
Local time is now:      Sun Apr 15 11:49:03 UTC 2007.
Universal Time is now:  Sun Apr 15 11:49:03 UTC 2007.
Run 'tzconfig' if you wish to change it.

The first few lines of bootstrap read:

Selecting previously deselected package base-files.
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_4ubuntu2_i386.deb) ...

And continue on through a slew of _i386.deb's for some pretty "setup" like stuff: libc6, perl-base, debconf and base-passwd

Thanks for the input guys!

It sure would be nice if this kind of information were saved somewhere. I hate to say it, but I know Windows keeps an install log of Windows from the first installation. At least the hand installed ones do (not the mirrored and pushed installs that OEMs use).

---

### Post by john.nicholls on 2007-07-10
> **psyopper said:**
> So it's been about three months since I installed Ubuntu, but I can't remember exactly when. I recall a random post on here at one point where someone told someone else they could check the date when the installed Linux by looking at something in /var/log (I think).

I now it's not "support" but it is "Absolute Beginner"...

Thanks!

Have a look at the files in /var/log/installer.

---

### Post by dptxp on 2007-07-10
Maybe you can see when you made the partitions, especially the /.

---

### Post by psyopper on 2007-07-11
> **dptxp said:**
> Maybe you can see when you made the partitions, especially the /.

/initrd shows a modified date of Sun 15 Apr 2007 04:48:50 AM PDT which works with the GMT conversion to match up with the other dates I already found

/mnt shows a modified date of Thu 12 Apr 2007 02:11:34 AM PDT. Seems the earliest of the bunch, but the other dates seem more realistic based on their consistency.

How do I check the date created on / ?

---

