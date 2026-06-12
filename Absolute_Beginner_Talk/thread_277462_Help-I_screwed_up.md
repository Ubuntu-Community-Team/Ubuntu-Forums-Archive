---
title: "Help-I screwed up"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by morr on 2006-10-14
hi, today I tried to install new drivers for my ATI graphics card, using the 
sudo dpkg-reconfigure xserver-xorg command. Stupidly enough, I changed more than just the drivers; somehow I managed to screw up my keyboard so that I can only use numbers and a few weird signs. The big problem is that when I rebooted I couldn't log in since I can't use any letters. I have tried what little I could think of, I entered the recovery mode and typed the same command there( keyboard works just fine in recovery mode) but it doesn't work but says something like 
dpkg: need an action option

Please please can somebody help me to either restore or reconfigure my keyboard!

---

### Post by morr on 2006-10-14
hmm by patting my computer desperately and trying with the same command again, all of a sudden it worked.Eureka! And the grapics card too! But not the delete post..........:KS :KS :KS :KS :KS :KS :KS

---

### Post by Haegin on 2006-10-14
Impressive! How about mounting the drive from the recovery console and changing the keyboard settings in the /etc/X11/xorg.conf file on the mounted partition.

---

