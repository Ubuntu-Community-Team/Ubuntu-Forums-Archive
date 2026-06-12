---
title: "Boot problem after installing updates"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by dabsan on 2008-02-05
Ubuntu 7.10, kernel 2.6.22-14-generic

Today I installed some updates from the automatic update manager. After installing them there was message to restart my computer. After restarting the computer the grub menu appears OK and the Ubuntu splash screen with orange loading bar appears and after the bar completes loading the following messages appear on the screen :-

starting anac(h)ronistic cron anacron 
starting deferred execution scheduler atd
starting periodic command scheduler crond
Enabling additional executable binary formats binfmt-support
Checking battery state...
Running local boot scripts (/etc/rc.local) 

Then the computer blank screens ......... 

Hope someone can help me.
Many Thanks

---

### Post by spydon on 2008-02-05
Can you boot into the old kernel from GRUB?

---

### Post by dabsan on 2008-02-05
No only have ubuntu 7.10, kernel 2.6.22-14-generic on my grub list.

---

### Post by dabsan on 2008-02-05
My Grub list :- 

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14 (recovery Mode)
Ubuntu 7.10, memtest+86
Other operating systems
Microsoft WindowsXP Professional

---

### Post by seventhc on 2008-02-05
I had a problem too, after the update I rebooted. It showed the 3 second timeout then when it went to boot I just got a blank screen and it just hung there. I rebooted into recovery and checked grub it looked the same to me so I left it. Rebooted, hang*** finally I just let it sit there and after a long time it finally did show me the login screen. I was thinking maybe it was just going through a reconfiguration or something but I'm really not to sure. Haven't rebooted since. ;)
I'd suggest to try booting up and wait it out for a while, my blank screen eventually came back to life. :) I'm not sure how long it took exactly but I think at least 10 minutes and possibly up to 20. 10 sounds more reasonable though.

---

### Post by dabsan on 2008-02-05
I tried leaving it for about 20mins but nothing happened. Really hope I can get this fixed. 
Any more ideas? Thanks.

---

### Post by seventhc on 2008-02-05
here is someone else that had a problem after the update..they get an error that you didn't get but it's still worth a look.
[http://ubuntuforums.org/showthread.php?t=687856](http://ubuntuforums.org/showthread.php?t=687856)

---

### Post by dabsan on 2008-02-05
Still not sure how to fix this problem.

---

### Post by dabsan on 2008-02-06
Well, I found out the problem. It was Envy, I was using the Nvidia driver installed by Envy and it must have conflicted with the latest Ubuntu updates. After removing the drivers installed by Envy the updates installed ok :)

---

