---
title: "Please Help Me???!!!!!"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by j_cutt on 2008-04-10
well i know i'll get laughed at by some but here is my prob. I have just decided to go to ubuntu from windows xp. i am not the most computer literate person by any means. this being said i figured the best way to learn was to dive head first into it. i downloaded ubuntu 7.10, burned it to disk, ran the disk on my computer, installed, when asked how much space i went all out and used complete on the partition. ( not well thought out)....
here is my problem the screen on my laptop is out so i use another monitor. i can run ubuntu from the disk in safe graffics mode but when i hit install or start i get the black screen. is there any way to get ubuntu to run from my hard drive and still use the external monitor????   ( my laptop monitor is VERY broken)

---

### Post by st33med on 2008-04-10
Perhaps you might want to try the alterante cd instead. It installs by text mode instead of using the GUI, and, If I am right, Xorg is loading on the default screen, which is why you can't see anything.

To download the alternate cd, click the check box at the Ubuntu download screen saying something about the Alternate CD.

---

### Post by spiderbatdad on 2008-04-10
You might check your system bios to specify a monitor.
Unless you can get a command line and feel comfortable navigating the file system and editing configuration files.

---

### Post by j_cutt on 2008-04-10
well that is my main prob my default screen is shot. i have to use the extra monitor just to use the comp. (sucks!!) i will try the other download though. As for the second comment i would just about try anything. i can get to a command promp. but i am a computer illiterate fool. i wouldn't even know where to start. i am good at following instructions if anyone knows what to do.

---

### Post by spiderbatdad on 2008-04-10
well...login on your terminal and enter```
sudo nano /etc/X11/xorg.conf
```
post back here on the computer you're using and let us know if you see a configuration file...or a blank file.
And what is your graphics card?

---

### Post by spiderbatdad on 2008-04-10
More than likely there is a key combination to enable the second monitr for your laptop...like fn-f3 on mine.

---

### Post by j_cutt on 2008-04-10
yes that has brought up the config. file and my graffics chip is ATI Radeon Xpress 200. not the best but its all i have. so any ideas where to go now?

---

