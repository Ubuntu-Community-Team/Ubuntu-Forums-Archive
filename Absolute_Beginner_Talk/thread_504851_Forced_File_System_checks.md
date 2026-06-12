---
title: "Forced File System checks"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Dennis N on 2007-07-19
I find that after being booted 35 times, and again after another 35 boots, I receive this message as Ubuntu starts up:

fsck 1.40-WIP (14 Nov 2006)
os_part has been mounted 35 times without being checked, check forced.

Then, for the next several minutes a check is performed (with a progress bar and percent completed). After this check, booting continues normally. 

Is this standard behavior for Ubuntu? No errors are indicated on the screen - all prior steps in the process that I can see are marked OK. (the last being 'activating swap') 

I am wondering if and how this forced check can be turned off, or at least done less frequently? It takes several minutes to complete.

system: Dell 1505N, Ubuntu 7.04

Thanks.

---

### Post by Daveth on 2007-07-19
it is a desirable feature of the filestsystem rather than a consequence of any error or anything you may have done. Treat it as a fringe benefit!

---

### Post by RobN on 2007-07-19
Is there a way to trigger this check manually? That way you'd have a little more control over when to lose that time on startup, rather than having it crop up seemingly at randum, potentially at a very undesirable time.

There have been times I've suspected something may be wrong and need a check, and I don't know how to fire one off. Windows finally has a QUI to trigger a chkdsk on startup...is there one hiding somewhere in ubuntu that I'm missing?

Likewise, is there a means to cancel this check on startup? Years ago, using Windows NT 3.51, we had an enormous hard drive (for the time, anyway) where a normal chkdsk took 4 hours to complete. We had a problem, and after 28 hours it still hadn't completed. At the time you couldn't reboot to abort the process, because it would just start from scratch all over again -- back then there was no "this will start in 10 seconds unless you press a key" prompt before chkdsk started. Without a similar "I'm smarter than the machine and I don't want it to run the check right now" option in Ubuntu, I can see the same thing happening to somebody some day.

---

### Post by ramjet_1953 on 2007-07-19
There is a package called [COLOR="Blue"]bonager[/COLOR] that allows you to postpone the scan.

It puts an icon in your top toolbar and tells you of the number of boots until the next scan.

Follow this link for full information: [http://ubuntuforums.org/showthread.php?t=295262](http://ubuntuforums.org/showthread.php?t=295262)

Regards,
Roger :cool:

---

### Post by yabbadabbadont on 2007-07-19
To force a filesystem check on next boot, simply "touch" a file called "forcefsck" in the root directory of the filesystem to be checked.  Example: ```
sudo touch /home/forcefsck
``` would force the /home filesystem to be checked on the next boot.

---

