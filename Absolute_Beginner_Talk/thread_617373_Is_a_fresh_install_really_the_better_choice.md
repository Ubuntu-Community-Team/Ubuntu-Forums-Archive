---
title: "Is a fresh install really the better choice?"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-11-19
So I just burned an ISO Image of Ubuntu Studio. Figured I'd check it out. Now, I recently redid my system. I dual boot with Win2kPro. Whenever I reinstall Ubuntu to a new version, my boot loader gets messed up. I have no idea how to fix this, and I've posted around a dozen threads about it so if you know how, tell me!!

Anyway, so until I get an answer I just expect to redo windows with ubuntu whenever I get a new version. I just put the dvd in for ubuntu studio and it prompted me if I wanted to upgrade.

Like two years ago when Edgy was hot stuff, I remember people saying the upgrade way to get the new version isn't as good as a new fresh install. Is that true?

---

### Post by dpar on 2007-11-19
I've done both with no problems, but a fresh install does tend to give you a 'leaner' system by getting rid of a lot of unused leftover junk from the old install.

---

### Post by sports fan Matt on 2007-11-19
To tell you the truth..I kind of agree a fresh install is a good thing because of the last comments--however, im not ALL that tech savvy but yeah i agree, it realeases the old files and whatnot

---

### Post by Roasted on 2007-11-19
I was browsing around here... I know once I reinstall Ubuntu Studio that I'll get partition read errors on the boot screen. Soooo I just have to reinstall grub? Right? I could have sworn I did that before, but maybe I goofed it up.

---

### Post by philinux on 2007-11-19
A reinstall should be no probs. But I would move home to its own partition it's a much neater solution.

---

### Post by sports fan Matt on 2007-11-19
What is ubuntu Studio?  and what are the differences between that and Ubuntu if any?

---

### Post by dgray_from_dc on 2007-11-19
I had hell with the Dapper to Edgy upgrade as outlined in this thread [http://ubuntuforums.org/showthread.php?t=310190](http://ubuntuforums.org/showthread.php?t=310190)

I have to say though that afterward (Edgy to Feisty) the transition went without a hitch.  I dual-boot with XP and experienced no hiccups during the upgrade.  Fresh install is cleaner but if you like to tweak settings and preferences like I do, it can be difficult to remember all of the apps and applets that were in place and how they were set up.

I've been using Ubuntu since around the Hoary-Breezy transition.  I have seen great improvement since then and have become confident in its' ability to upgrade itself.  (I am however a little biased by my laziness)

---

### Post by Roasted on 2007-11-19
> **philinux said:**
> A reinstall should be no probs. But I would move home to its own partition it's a much neater solution.

Oh I already did. But when I upgraded from Feisty to Gutsy, all that I formatted was my root dir to install the new OS on that partition. Then GRUB went to **** and I had to redo Windows too because the grub-reinstall-guide I had somehow didn't work. *shrugs* 

I just wanted to see if I could get around that issue...

---

### Post by chris_nava on 2007-11-19
I prefer to perform a fresh install whenever I upgrade my OS.  (After backing up the existing partition of course.)  I know that this is a lot of work and not always an option but when available is clearly the "cleaner" choice.

You end up having a system that more closely matches the default settings for the new OS version.  
The beauty of this is that you benefit from the large amount of beta testing that goes into pushing a new version and eliminate configuration incompatibility issues that may not have been accounted for in the upgrade script.

It also forces you to reinstall and configure your applications (and to decide which ones you truly still need) thus eliminating cruft in your custom configuration as well.  You DID document which applications you installed, didn't you?  ;-)

Edit:  And just in case my documentation is not up to date... Does anyone know of a way to generate a list of the applications installed by hand?  Like a list of all the packages installed via "apt-get install _____"  I'm not concerned with dependencies just the things I explicitly installed.

---

