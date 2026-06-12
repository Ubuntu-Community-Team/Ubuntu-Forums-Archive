---
title: "Problem I've never seen before"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Sable683 on 2007-05-30
I am hoping someone here can help me...  I have been using Ubuntu for about 8 months now and the system has ran flawlessly until now. When I turn on my machine, it ran for 8 hours and all I got was a blank screen with the cursor in "working mode", the flashing circle. 
I downloaded the Feisty Fawn live CD and attempted to run it, but now I get the following error message:

/bin/sh: can't access tty; job control turned off
(initramfs)

Any one out there who can tell me how to correct this, I would greatly appreciate it. I don't know how "job control" was turned off.

Thanks,
John

EDIT - I did search this forum for anyone else who had this problem, but there were no solutions that worked. 
BTW - I am running a Dell Inspiron 2650 w/ 512 MB Ram, 30 GB HDD and there are 3 partitions that are set at /, /usr & /home. There is no windows partition on this hard drive, it is solely running Ubuntu

---

### Post by EagleRock on 2007-05-30
The job control error is due to an issue with drive hardware.  You can fix this issue by adding "irqpoll" to the boot options on the Live CD.  Hit F6 when the boot options come up to pull up the area where you can add it.  There are quite a few threads about this issue already, some of which I linked below:

[http://ubuntuforums.org/showthread.php?t=415009&highlight=job+control+turned+off](http://ubuntuforums.org/showthread.php?t=415009&highlight=job+control+turned+off)

[http://ubuntuforums.org/showthread.php?t=456838&highlight=job+control+turned+off](http://ubuntuforums.org/showthread.php?t=456838&highlight=job+control+turned+off)

---

### Post by Sable683 on 2007-05-30
Okay, I attempted to try the "F6" and adding irqpoll, but that did not work for me, I got the same error again. I also checked the floppy drive, it does not appear to be seeking it on the boot. Is it possible to downgrade to an older Kernel? And if so, how?

And another thing, last night before I shut down the laptop, I did install all of the updates that were recommended.

Any and all help is appreciated! EagleRock, I tried those links, but none of the suggestions worked.

John

---

