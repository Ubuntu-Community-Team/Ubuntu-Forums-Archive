---
title: "Hibernate/suspend on MacBook Pro 13&quot;"
date: 2017-01-11
forum: Apple Hardware Users
---

### Post by vegarab on 2017-01-11
Hi.

I installed linux ubuntu (my first linux install) on my MacBook a few days ago.
One of the major problems is being able to close the laptop in any way, and continue my work without a reboot.
I have tried suspend, but it only works if I press the power-button or open the lid again (if I closed it to engage in suspend) within 1-2 minutes. If I try to resume later than this, the lock-screen shows for a split second before the screen goes black. The machine is still powered on, using power (Apple logo and keyboard is still lit). Only fix from here is to forcefully reboot the machine.

Because of this time-based behaviour, I assume that the problem lies with hibernation, since the machine would go to hibernation after x time in suspend, am I correct?

Alright, so I checked around on hibernation and figured I need a swap-drive. I didnt have one, so I made one.

I used the first reply here as my guide: [http://askubuntu.com/questions/33697/how-do-i-add-a-swap-partition-after-system-installation](http://askubuntu.com/questions/33697/how-do-i-add-a-swap-partition-after-system-installation)
Funny thing is, when I do the 
```
sudo blkid | grep swap
```
command, I can clearly see the UUID of my swap drive, labelled as a swap-drive.
However, 
```
swapon -s
```
does nothing at all. Just jumps to next line in terminal and that is it.. ?

I have also tried using dconf Editor to change the actions on lid-closing, and also tried to follow this guide: [https://ubuntuforums.org/showthread.php?t=2329877](https://ubuntuforums.org/showthread.php?t=2329877) but with no luck.

Any clues?

---

### Post by howefield on 2017-01-11
Thread moved to the "*Apple Hardware Users*" forum.

---

