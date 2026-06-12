---
title: "GRUB Problems"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by bart_simpson on 2007-07-20
Ok, I've installed Ubuntu Feisty Fawn onto my computer's second hard drive. After getting it installed, I find out that GRUB failed to install properly for whatever reason. With a friend I go over various methods of installing GRUB through the Live CD, but all I get when I boot up my computer are Error 21 messages. If anyone has any ideas as to why this is happening, I am all ears. By the way, specs on my computers setup and whatnot will be forthcoming, I still need said friend to help me get the information for it.

---

### Post by ravenwere on 2007-07-20
Follow this thread for info:
[http://www.linuxquestions.org/questions/showthread.php?t=552043](http://www.linuxquestions.org/questions/showthread.php?t=552043)

This should probably solve the issue.

Error 21 - selected disk does not exist

Regards,
R

---

### Post by bart_simpson on 2007-07-21
Okay thanks, I've got a couple of ideas now that I'm going to try out and if they don't work, my next post will be detailing all my specs and order of drives and whatnot.

---

### Post by confused57 on 2007-07-21
Here's some possible solutions for grub error 21:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

I've experienced grub error 21 on a Dell Dimension 4550, I had to go into bios and set the slave drive IDE controller from "off" to "auto", after I installed a 2nd hard drive.

---

