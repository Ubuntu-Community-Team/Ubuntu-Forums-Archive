---
title: "A Rant &amp; a Plea for Help"
date: 2011-06-21
forum: Apple Hardware Users
---

### Post by moore.bryan on 2011-06-21
**_Background_**
I've tried and tried to get any program (dvd::rip, acidrip, VLC, etc.) to rip my DVDs to files on my "ancient" iMac G4 FlowerPot running Debian Squeeze and Openbox, but to no avail.

**_Rant_**
Why is there not a single "turnkey" program for Linux for ripping DVDs? They all *claim* they are, but **none of them are**. It seems like such a simple request. I've even tried all the command-line versions of random scripts out there and **none**, as in **not one** worked with **any** of my DVDs.

**_Request for Help_**
I'm not looking to rip a DVD, upload it, and have others thieve it, stealing money from the needy pockets of production CEOs; I have no problem with that, though, it's just not what I'm trying to do. I'm not really looking for responses like "blame the corporations, bro" or other useless comments... all I'm looking for is a 100% effective, guaranteed to work method on my PPC iMac to rip a DVD.

Any takers?

---

### Post by CoreyB. on 2011-06-21
I don't know about the PPC Ubuntu repos (never used it), but K9Copy seems to be capable of doing the job.

Note, I've never used K9Copy either.

Post back whether or not it works for you!


EDIT: I looked and it seems K9Copy *is* in the Natty PPC repos, so definitely give that a try.

---

### Post by moore.bryan on 2011-06-21
Tried K9 before and it doesn't do as advertised, at least on PPC; all it gave me was an 8mb empty file.

---

### Post by CoreyB. on 2011-06-23
I tried *The Departed* using K9Copy and it compressed it to a ~4.5 GB image, but I'm sure if I looked more carefully I could have it not compress it.

Maybe recheck your settings on K9copy.

---

### Post by holastickboy on 2011-06-23
I personally never had any issues with copying dvds, but then I admit I have never used a PPC Linux distro before.  Perhaps it is something to do with that?  Are the packages you are using have current PPC versions in line with the x86 versions?

---

### Post by moore.bryan on 2011-06-23
> **CoreyB. said:**
> I tried *The Departed* using K9Copy and it compressed it to a ~4.5 GB image, but I'm sure if I looked more carefully I could have it not compress it.

Maybe recheck your settings on K9copy.
No matter what I do, I can't seem to get K9Copy to work; in fact, it won't recognize there's a DVD in the drive... even AcidRip and dvd::rip do that!

> **holastickboy said:**
> I personally never had any issues with copying dvds, but then I admit I have never used a PPC Linux distro before.  Perhaps it is something to do with that?  Are the packages you are using have current PPC versions in line with the x86 versions?
I'm beginning to think this may be the culprit. All the PPC versions are the same as or similar to the x86 ones, it just won't work no matter what.

---

### Post by handy on 2011-06-23
Have you tried Handbrake for PPC:

[http://mac.oldapps.com/handbrake.php?old_handbrake=22](http://mac.oldapps.com/handbrake.php?old_handbrake=22)

---

### Post by LtPitt on 2011-06-24
I may be pointing to stupid things because it looks like you've been fighting with the problem already but...
Do you have all the codecs and decss necessary to rip the dvd?

---

### Post by linuxopjemac on 2011-06-24
I would first add the medibuntu repository:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and install ubuntu-restricted-extra:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Hope this helps...

---

### Post by moore.bryan on 2011-06-25
> **handy said:**
> Have you tried Handbrake for PPC:

[http://mac.oldapps.com/handbrake.php?old_handbrake=22](http://mac.oldapps.com/handbrake.php?old_handbrake=22)
Hmm... a while back I tried to compile Handbrake from source because there wasn't a PPC package, but maybe there's one now? The wesbite looks like it's for Mac-only, though...

> **LtPitt said:**
> I may be pointing to stupid things because it looks like you've been fighting with the problem already but...
Do you have all the codecs and decss necessary to rip the dvd?
Yeah, I have... thankfully those were the first things I doubled-checked! :-) Thanks for the suggestion, though; I've often found the simplest answer is often the most likely culprit.

> **linuxopjemac said:**
> I would first add the medibuntu repository:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and install ubuntu-restricted-extra:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Hope this helps...
Not running on Ubuntu (Debian install with Openbox) makes this a little more of an issue. I've already installed via the Debian Multimedia repo all those things contained in the ubuntu-restricted-extras metapackage.

---

