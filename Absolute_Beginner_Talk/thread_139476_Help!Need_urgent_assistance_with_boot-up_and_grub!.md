---
title: "Help!Need urgent assistance with boot-up and grub!"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by hovmod on 2006-03-04
Hi.

I decided to re-install ubuntu, and somewhere in the middle of that something went wrong.
The partitioner didn't like my choices, and I aborted the installation.

Now the GRUB start-up menu is gone, and I have two hours to set up the computer to boot in windows so my wife has a computer while I'm away.

How do I fix this?

GRUB says error 15. When I boot on the ubuntu live CD and mount the ext3 partition  there's only an empty folder called 'lost+found'.

How do I fix this?

---

### Post by yatesDELTA on 2006-03-04
to be honest id reinstall xp. or whatever you use. i only just got linux to work. do you have acses to another computor?
i suggest you download and write the disk again . it will take about 4 hours but hey

---

### Post by Herman on 2006-03-04
If you just re-install Ubuntu it should only take about half and hour on an average modern-day computer, that would be the easiest, fastest and best.
You could instead look at some of these [uninstall methods here]("http://users.bigpond.net.au/hermanzone/p18.htm") for restoring your old boot sector to boot just Windows again if you wish -the choice is yours. Good Luck, from Herman :-D

---

### Post by hovmod on 2006-03-04
Thanks a lot.

I'll report back... :)

---

### Post by hovmod on 2006-03-04
Now fixed! Phew.


Thanks for your help.

---

### Post by Aewheros on 2006-03-04
You should boot on the windows partition if that one is the first one on the list.

Edit the linux partition. You should see a path like "/dev/sda6" or whatever number you've got. That's the option you requested, change it to root file system. If edited properly, you should only see a "/". Good luck.

---

