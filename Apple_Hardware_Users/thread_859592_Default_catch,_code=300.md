---
title: "Default catch, code=300"
date: 2008-07-14
forum: Apple Hardware Users
---

### Post by Super TWiT on 2008-07-14
When trying to dual boot Ubuntu and OS X 10.3, I receive the Default catch, code=300 errors all over the screen.  I have had both Ubuntu and OS X 10.3 on the computer individually, but I can't seem to have them both on at once.  The computer is an iMac g3 tray loader if that makes any difference.  Any ideas?

---

### Post by Super TWiT on 2008-07-18
Anyone?

---

### Post by stream303 on 2008-07-19
Do you have an upgraded hard drive that is larger than 8gb?  No matter what, you must keep your root / boot partitions for either osx or Ubuntu under 8gb for that machine -- make it 7gb to be safe and easy to remember.  I'd probably put most of Ubuntu under 8gb, and partition the rest of the drive for /home

Check out this archived ppc thread with a link to Apple docs regarding the default-catch code=300 issue:

[http://ubuntuforums.org/showthread.php?t=590440](http://ubuntuforums.org/showthread.php?t=590440)

---

### Post by Super TWiT on 2008-07-20
All of my root partitions are within 8 GB.  Could Yaboot be detecting the wrong drive to nstall to? As I have other partitions that aren't within 8 GB.

---

