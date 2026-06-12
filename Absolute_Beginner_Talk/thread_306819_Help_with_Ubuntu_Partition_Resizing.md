---
title: "Help with Ubuntu Partition Resizing"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by ShoulderKnight on 2006-11-25
Everything was going great with the Unbuntu install until I chose option one for it to resize my partition. 

Well the mouse cursor still moves and its been about an hour and a half.  How long does it take to free up 30 gigs or is it frozen?  Don't want to restart now because who knows what the effect will be.

---

### Post by aidanr on 2006-11-25
yeah that sounds like way too long, that'd take 20 minutes at most for me. i've had this happen to me before though with the gparted live cd, it just froze up during partitioning, so i gritted my teeth and did a hard reboot, luckily the partitioning operation had finished and it was just the gui that had crashed, so no loss of data or damage to the disk. try putting your ear up to the harddrive and listen for harddrive activity, also you could try the alt+sysrq+[s/u/b] commands, but i'm not sure if they are enabled on the live cd, your call, good luck

edit:// you can also hit ctrl+alt+F6 to get a shell, login and type "top" to see whats running and "ps -A" to see a list of processes, you can also try to unmount the disk from here safely etc

---

