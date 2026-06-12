---
title: "segmentation fault"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Timmy66 on 2007-06-02
Will somebody please explain what a segmentation fault is and how can I fix it.I had to hit the reset button on my system 9 times today to get it to finally boot up.I have made to the switch to ubuntu(feisty fawn) and have no plans on going back to microjunk.I just have a few bugs to work out.

---

### Post by AnRa on 2007-06-02
You have a good explanation here: [Segmentation fault](http://en.wikipedia.org/wiki/Segmentation_fault)

---

### Post by wpshooter on 2007-06-02
Have you ran memtest to see if you have any faulty memory in your system ?

---

### Post by Skrynesaver on 2007-06-02
Which application is failing with this message?

---

### Post by zanglang on 2007-06-02
Just adding to the questions here, when and where are you seeing this message (e.g. when booting up, while logging in)? What kind of system are you installing Feisty on?

---

### Post by DraikX on 2007-11-10
I get the following error message when trying to reinstall AmaroK (for some reason it won't load from K Menu or from Katapult):

/bin/sh: line 1:  8270 Segmentation fault      (core dumped) /usr/sbin/dpkg-preconfigure --apt
(Reading database ... 246648 files and directories currently installed.)
Preparing to replace amarok 2:1.4.7-0ubuntu3 (using .../amarok_2%3a1.4.7-0ubuntu3_i386.deb) ...
Unpacking replacement amarok ...
Setting up amarok (2:1.4.7-0ubuntu3) ...

dpkg run finished!


This is from Adept. I've reinstalled dpkg, AmaroK, libc6, and a few other packages. All of which I already have installed. I am running Gutsy Gibbon.

---

