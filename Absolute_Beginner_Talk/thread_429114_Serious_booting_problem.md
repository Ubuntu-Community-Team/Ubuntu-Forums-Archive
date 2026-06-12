---
title: "Serious booting problem"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by stellarhn on 2007-04-30
Okay I'm very new to Ubuntu and Linux and just downloaded Ubuntu. I'll try to be as descriptive as possible, bare with me since I'm still not familiar with all of the terms. I ran the live CD. I then installed Ubuntu on a external hard drive. I have windows xp on my internal hard drive, and before I installed Ubuntu I installed System Commander in order to choose the operating system. So after the install of ubuntu I restarted my machine without the disk, and I get the following message: 
GRUB LOADING STAGE 1.5
GRUB LOADING PLEASE WAIT...
ERROR 2
I get stuck here, the only thing I can do is press control+alt+delete to restart, but it comes back to this same error. All I can do to get on my computer is continue to run ubuntu from the live cd, which I am doing now. 
I should probably note, when I start ubuntu from the disk, during the screen with all the text I see a message which is something like: No_Reboot flag disabled by hardware
Not sure if this is relevant to my problem. 
My main concern is at least being able to get back on Windows. I know my other hard drive and windows still exists because I can browse through it on ubuntu. I'm not able to run a system restore with f10 at startup though, I get the errors mentioned previously. 
I'm sorry if this is something you've heard before, I've been reading other topics but I get very confused with a lot of the terminology. If I can get this problem fixed I shall do more research to be able to properly do an install. 
If anyone can help me out I would greatly appreciate it, it would mean a lot. I fear I have ruined my system because I got excited and started installing things right away. 
Any ideas, hints, suggestions?? I'm pretty desperate. 
Thanks a lot in advance, 
-Nic

---

### Post by phiphedog on 2007-05-01
It sounds like you boot loader is failing to load (GRUB) and may be corrupted. If this is a fresh install try installing it again.

---

### Post by stellarhn on 2007-05-01
> **phiphedog said:**
> It sounds like you boot loader is failing to load (GRUB) and may be corrupted. If this is a fresh install try installing it again.

Install the whole thing again or just GRUB? Wondering because I never actually installed GRUB, I thought it automatically did when I installed ubuntu? If I need to reinstall GRUB how do I go about this?
Thanks a lot.
-nic

---

### Post by duglaswb on 2007-05-01
Whenever I have a problem with grub and need to reinstall I turn to this thread over on the Fedora forums.  

[http://forums.fedoraforum.org/showthread.php?t=975]("http://forums.fedoraforum.org/showthread.php?t=975")

Shouldn't be any different with ubunutu.

---

### Post by stellarhn on 2007-05-01
> **duglaswb said:**
> Whenever I have a problem with grub and need to reinstall I turn to this thread over on the Fedora forums.  

[http://forums.fedoraforum.org/showthread.php?t=975]("http://forums.fedoraforum.org/showthread.php?t=975")

Shouldn't be any different with ubunutu.

Thanks I will give that a try., If anything though I'm wondering if anyone can tell me how to just get rid of everything and go back to Windows for now? I'm more concerned with getting my computer back to normal than fixing ubuntu at this point. I will paypal someone if I can get good instructions, shows how desperate I am. 
Thanks, 
Nic

---

### Post by oilchangeguy on 2007-05-01
try this:
In Windows XP, you can uninstall GRUB as follows:

Boot from the Windows XP CD and press the "R" key during the setup in order to start the Recovery Console. Select your Windows XP installation from the list and enter the administrator password. At the input prompt, enter the command "FIXMBR" and confirm the query with "y". The MBR will be rewritten and GRUB will be uninstalled. Press "exit" to reboot the computer. don't use the " with your commands. and i belive you'll have to type exit at the prompt and press enter to reboot.

---

### Post by stellarhn on 2007-05-01
> **oilchangeguy said:**
> try this:
In Windows XP, you can uninstall GRUB as follows:

Boot from the Windows XP CD and press the "R" key during the setup in order to start the Recovery Console. Select your Windows XP installation from the list and enter the administrator password. At the input prompt, enter the command "FIXMBR" and confirm the query with "y". The MBR will be rewritten and GRUB will be uninstalled. Press "exit" to reboot the computer. don't use the " with your commands. and i belive you'll have to type exit at the prompt and press enter to reboot.

Thanks a lot, I will try that, however I can't find my original xp cd. Hopefully I can do that. Thanks again very much, I'll let you know how that goes if I can. 
-nic

---

### Post by Duck2006 on 2007-05-01
[http://users.bigpond.net.au/hermanzone/p15.htm#If_you_want_to_restore_the_Windows_boot_sector](http://users.bigpond.net.au/hermanzone/p15.htm#If_you_want_to_restore_the_Windows_boot_sector)

This sould help in fixing your mbr so you can boot to windozes

---

### Post by oilchangeguy on 2007-05-01
if you can't find your windows disc, check this out:
[http://support.microsoft.com/?kbid=310994](http://support.microsoft.com/?kbid=310994)

---

### Post by stellarhn on 2007-05-01
Thank you all very much, I'll keep trying.

---

