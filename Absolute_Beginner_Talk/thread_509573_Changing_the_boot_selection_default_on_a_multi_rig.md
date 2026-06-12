---
title: "Changing the boot selection default on a multi rig"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by matrix99x on 2007-07-25
Hello, I am a PC user who recently installed a dual OS system and it works great, i have both XP and Ubuntu on seperate partions and the Ubuntu controlls the boot section, i was wondering how do you edit the boot selector to have XP as the default OS. I worked a little with OpenSuse but they have a different boot loader.

---

### Post by MQMike on 2007-07-25
Look at the second post of my How-To.

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

In Ubuntu, when you want to edit the boot menu (/boot/grub/menu.lst), you have to use
sudo gedit . . .
instead of the Kubuntu way (kdesu kate, or sudo kate, etc.).  Some of these "reminders" are contained in the first post, at the end, too.

---

