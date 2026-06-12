---
title: "[SOLVED] Partition Modifications, Post-Install"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by v.alari on 2007-12-11
I just installed Ubuntu and manually created 2 Partitions on my HDD (1swap, 1 for filesystem). This left a significantly decreased windows partition and a small linux partition used to load windows (I thought that was ironic and quite funny, lol).

So next I tried to create a fifth partition for data but linux doesnt like more than four anymore than windows does. However, I do know this is possible as I have read here about a user running ten partitions. What I want to do is edit my partition table in such a way that the following requirements are met:

1. /boot moved to a new separate partition

2. /home moved to a new separate partition

3. the small linux windows loader and the windows partition on my boot list (so I can re-install the windows partition with the small linux partition etc. etc.) 

4. / moved to a new separate partition

5. /usr in the big partition

If any of these ideas seem wrong please inform, however #3 is required because until I have no need of windows (ie. I get my windows games etc. to run properly under wine) I will need (I know, I know. Its windows) windows.

Please note I dont care that windows sucks, I have installed OS's before, I am a huge fan of CLI, I know what a partition is, and I grew up with C64 and DOS. I just need to know how to do more than four, how to move these core parts to their own partition, and how to edit my boot table in such a way that everything is on it not just one partition or another which I can do.

---

### Post by Harpoon on 2007-12-11
Unfortunately, there is that pesky 4 partition limit.  Fortunately, you *can* have more than four partitions.  

Assuming a complete reinstall, you could, for example:
Create 1 partition for Windows;
Create 1 partition for shared data between windows and linux
Create 1 partition for you linux OS
Create 1 partition for swap.

OK, that's 4.

Now select, say, the first windows partition;  Inside that you can create more logical partitions - - e.g. one for system an one for data).

You can do the same with the linux OS partition, and so on.

What you get are a lot a=of partitions set up the way you want, but with often goofy looking "names" because the partition numbers (hda1, sda5) are assigned in such a way that you may find it difficut to tell one from the other just by looking.

I suggest you download a copy of gparted live cd, and boot into that to do the partition work.  Great program.

---

### Post by v.alari on 2007-12-11
RightO
Thanks

---

