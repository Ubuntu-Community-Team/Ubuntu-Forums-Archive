---
title: "partitioning"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by rgreen23 on 2007-09-12
Hey there!
I just got a new computer with no operating system, so Ubuntu 6.06 was refered to me. I took up the offer but when I got to the partitioning part, my computer froze on step 5 out of 6. I have a Seagate Barracuda hardrive... I tried to look it up in the applications on the manual partition app., but it didn't recognize that I even have a hardrive, while it did recognize my jump drive.
What exactly is one to do?
-Rebecca

---

### Post by swoll1980 on 2007-09-12
Try fiesty 7.04 it's got more drivers built in to it and lots of other goodies not included in the lts version i'm running the gutsy tibe 5 on my desktop I wouldn't recommend it if it's your only pc but gutsy has been as smooth as silk for me so far.

---

### Post by dhughes on 2007-09-13
I've had the partitioning freeze up on me during an Ubuntu install, usually I just either start over and see if it works or I'll wipe the drive again using Darik's Boot and Nuke (DBAN) and/or I'll delete any partitions and recreate them again using Gparted or Parted Magic.

 No reasoning behind it but sometimes it works, my hardware is quite old (5 years) so I figure something is not quite right.

 One time I accidentally created partitions in a weird order and had started to install the OS on hda2 (I make a separate /home partition ) and not hda1. That caused some weird problems that were fixed by doing what I said above and making sure I installed the OS on hda1.

---

