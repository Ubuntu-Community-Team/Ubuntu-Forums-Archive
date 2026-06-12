---
title: "[SOLVED] Drive Volumes Not Visble"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-10-22
With one machine which dual boots with XP,  I hit the Upgrade button and Gutsy appeared without incident.

The operating system and most installed programs run.  No problem.

The problem is that hda1 and hdb1 which are the two drives cannot be browsed.  Hda1 is a mix of fat32 and ext3.  Hdb1 is fat32.   The fat32 partitions may be read when booted from XP but they are totally blank when viewed from Nautilus.

Thunderbird does not run.  The data files are held on hdb1 and Thunderbird apparently cannot see this drive and so does not launch.

Somewhere the obvious is standing out and shouting but I cannot see the wood for the trees at present.

Any suggestions at all?

---

### Post by benerivo on 2007-10-22
It sounds like they are both failing to mount in ubuntu. Have you checked your /etc/fstab file to see what the entries for these drives look like? Also try looking in 'Computer' from the naultilus menu, to see if they are visible.

---

### Post by expatCM on 2007-10-23
Good suggestion that one .....   quite a mess ....   something in the Gutsy install changed quite a lot of the volume identification and that was the cause of the problem.  I can see that there are a few other potential issues here but for the present I will leave them alone.   Perhaps on this machine I should have done a fresh install rather than an upgrade.

Thanks for the help :)

---

