---
title: "Virtual Box on Linux 7.04 - what does this error mean?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by letmein on 2007-06-12
I get this error when i try to start Virtual Box: [B]PIIX3 cannot attach drive to the Secondary Master.
[/B]
Was hoping someone could explain what this possible response (below) is to the problem above is, in English:

**That means that somehow the CD configuration was destroyed (or the permissions to the CD drive were somehow changed on the host OS - or the image file is no longer accessible). Secondary Master is currently always the VM's CD drive. So the easiest solution is to check the CD config and if necessary re-do it.**

---

### Post by HotShotDJ on 2007-06-12
It means you pooched the CD configuration in Virtual Box.  Check the CD/DVD-ROM configuration as well as the availability of any ISO image files you may have mounted in the past.

---

### Post by letmein on 2007-06-12
uhh...yeah...ok, what is it that i should be 'checking for' ?  It opened fine a handful of times, but today it gave that error.  The error which i have no idea what it means, the response to the error is equally confusing.  I know what pooched means....and i know what an iso image is...and i havent 'mounted' (whatever that means) any images in the past.  Is there a step by step method that qualifies the 'checking for' resolution?

---

### Post by HotShotDJ on 2007-06-13
1) Open VirtualBox
2) Highlight the "machine" that is giving you problems,
3) In the right panel, look for CD/DVD-ROM  -- click on it
4) Look at the options -- is "Mount CD/DVD Drive ticked? Is "Host CD/DVD Drive" or "ISO Image FIle" ticked?
5) Does the Host CD/DVD drive point to a valid device OR does the ISO Image File point to a valid image file?

Those are the only things I can think of that might correct your problem.

---

### Post by letmein on 2007-06-13
Mount CD/DVD Drive ticked? = Yes mount CD?DVD is indeed ticked
Is "Host CD/DVD Drive" ticked? = Yes, Host CD?DVD Drive is ticked
or "ISO Image FIle" ticked? = No, ISO image is not ticked
Does the Host CD/DVD drive point to a valid device? = Yes, it points to a valid device

What should i do now?

---

### Post by letmein on 2007-06-13
For anyone else who may or may experience this error...all i did was untick the CD/DVD checkbox...then restarted Virtualbox...then closed virutalbox and reticked the CD/DVD checkbox.  Also, some users had reported that adding and removed a flash drive, if a flash drive was used in the past also worked.  Anyway, thx!

---

### Post by HotShotDJ on 2007-06-14
I'm glad you got it sorted.  I was fresh out of ideas. :)

---

