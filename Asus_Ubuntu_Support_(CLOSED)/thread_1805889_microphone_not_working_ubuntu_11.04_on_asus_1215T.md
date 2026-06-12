---
title: "microphone not working ubuntu 11.04 on asus 1215T"
date: 2011-07-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ignorantprogrammer on 2011-07-16
Both the internal mic and plugged in mic that comes with headphones. It works sometimes, though. I tried my internal mic yesterday and it worked. It doesn't now. I checked alsamixer and sound preferences. They seem in okay settings.

---

### Post by freedomAboveAll on 2011-08-02
Hello, I am having same issue.

Have you noted the discussion in this thread:

[http://ubuntuforums.org/showthread.php?p=10332812](http://ubuntuforums.org/showthread.php?p=10332812)

---

### Post by r_mano on 2011-11-30
Seems the same as in ubuntuforums.org/showthread.php?p=11500623 and [http://ubuntuforums.org/showthread.php?p=11500627](http://ubuntuforums.org/showthread.php?p=11500627)

If you have still problems, please see [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/898081](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/898081) and add yourself to the bug.

---

### Post by r_mano on 2011-11-30
I tried the solution posted in the bug, following instructions from [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS) 

It works!

---

### Post by sk8brding on 2012-02-22
Thank you r_mano,

I have an ASUS UL20FT purchased in 2011.
Your DKMS solution was perfect.
I had the problem unsolved for months - the ALSA settings were not the answer - and in 5 minutes of reading your post my mic was up and working.
Until tonight I had been using 10.04.3 as the mic was working in it but now I am back experimenting with 11.10.
Really solid post and I would suggest if anyone has a recent PC this is a better solution than the others like ALSA MIXER etc. This really does work! Just install and shut down and start up again.

Why was this fix so hard to find for Ubuntu tho? Puppy Linux has a wizard which sorted my sound stuff out in 20 seconds...

---

### Post by r_mano on 2012-02-28
Thanks --- you're welcome. 

Sound and Linux have a very "interesting" story... ;-)

---

