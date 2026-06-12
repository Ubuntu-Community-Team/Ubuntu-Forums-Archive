---
title: "[SOLVED] Problems with Gurb"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by LinuxGEEK7288 on 2007-08-01
Okay so I've been reading a bunch of other posts and i can't seem to figure out how to fix my problem. What happened is, i Run a duel boot system Windows XP and Ubuntu using GRUB as my boot loader. All was fine until i added another Windows partition which got GRUB all out of sorts. Now ever time i boot i have to go in and tell it what partition to boot from. So what I'm asking is where do i go to edit the drive information in GRUB and have it stay that way? Also if this question has already been asked and i just missed it please tell me. Thanks

---

### Post by tonyr1988 on 2007-08-01
While in Ubuntu, open the file /boot/grub/menu.lst and copy/paste the output in a reply. Make sure you wrap it around Quote tags - it'll probably be long. Also, what are your partitions? Do you have two Windows, or is the other partition for something else?

---

### Post by LinuxGEEK7288 on 2007-08-06
Hey thanks for the location of that file i edited it and now it works great

---

