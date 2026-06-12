---
title: "New x64 Feisty install halts at 'Loading Hardware Drivers'"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by fastpakr on 2007-07-27
Just finished installing 64 bit Feisty on a Compaq F572us using the alternate CD.  I created a separate /home partition, for what that's worth.  It stopped booting with the progress bar at approx. the halfway point.  I rebooted and edited the boot command to disable the splash screen, and now it simply halts at:
* Loading hardware drivers...


Any ideas on where to go from here?  The 32 bit Live CD doesn't seem to boot either.  I'll grab the error message for that later.

[Hardware specs](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01069714&lc=en&cc=us&dlc=en&product=3441671&lang=en) from HP if that helps.

---

### Post by fastpakr on 2007-07-27
Looks like I'm not the only one...
[https://answers.launchpad.net/ubuntu/+question/9882](https://answers.launchpad.net/ubuntu/+question/9882)
[https://answers.launchpad.net/ubuntu/+question/9821](https://answers.launchpad.net/ubuntu/+question/9821)
[http://ubuntuforums.org/showthread.php?t=510781](http://ubuntuforums.org/showthread.php?t=510781)

---

### Post by fastpakr on 2007-07-27
I'm going to see if a Knoppix CD will boot properly.  Hopefully that will give me access to open the log file - maybe from there we can figure something out?

---

### Post by fastpakr on 2007-08-04
This is solved.  It appears that Ubuntu requires the 'noapic' option to boot in both 32 and 64 bit versions.  By one account, XUbuntu does NOT require that option.

---

