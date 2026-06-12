---
title: "installing ubuntu?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by acer56 on 2006-07-04
Hi i have ubuntu for mac but when i insert the disk into my apple mac it comes up showing me aload of folders but when i try and click on anything it says, computer doesnt know which application to open it with please choose? so how do i actualy install ubuntu?

---

### Post by Jagot on 2006-07-04
Do you have a PPC or an Intel Mac?

---

### Post by acer56 on 2006-07-04
PPC 10.3.9, i follow the instructions i insert it into my disk tray and restart the mac but it just loads up like normal.

---

### Post by Jagot on 2006-07-04
And you're holding do the 'c' key when it reboots?

---

### Post by acer56 on 2006-07-04
yeh i just tryed tht it comes up ubuntu and loads, then it comes up with all these sudo commands i can use, which is great but how do i get past that and into a graphic desktop?

---

### Post by acer56 on 2006-07-04
when the ubuntu progress bar finishes the screen ggoes black and says type sudo for commands ect.....how do i get past that and into a graphic desktop?

---

### Post by MiKuS on 2006-07-04
for me (i don't use a mac) but i'm sure the boot cd's "look" the same to the end user.

anyway, for me it brings up a menu of all the options i can choose, like "Start or install ubuntu"
"start ubuntu in safe graphics mode" and so on. just choose the top option, you should then be greeted with a desktop (which is ubuntu)

then just double click the install icon and fill out the qustions.

best of luck.

---

### Post by FredB on 2006-07-04
I remember !

Press c, then enter, and it will boot until it comes to graphic user interface.

---

### Post by acer56 on 2006-07-04
i do press c when i boot the mac up and it comes up with a graphic saying ubuntu and underneith and progress bar and underneith that aload of text loadibng with ok beside it then when tht finishes the screen goes black white writing appears saying linux ubuntu 6.06 copyright information and underneith that some text sayinf type sudo for admin commands type something else to do something esle and i cant get past this screen.
.

---

### Post by FredB on 2006-07-04
[QUOTE=acer56]i do press c when i boot the mac up and it comes up with a graphic saying ubuntu and underneith and progress bar and underneith that aload of text loadibng with ok beside it then when tht finishes the screen goes black white writing appears saying linux ubuntu 6.06 copyright information and underneith that some text sayinf type sudo for admin commands type something else to do something esle and i cant get past this screen.
.[/QUOTE]

Gnnn ?!

try to reboot, when you're on the first screen, try entering a video option like  "old" something, related to video display. Can't remember the name, but I think you'll find it ;)

---

### Post by acer56 on 2006-07-04
when the progress bar finishes its says cannot detect server x graphical it is likely that it is not set up correctly or something press yes to digonouise or no if i press either i still get diverted to this black screen

---

### Post by FredB on 2006-07-04
So, this is a linux boot option problem. I can't remember the real name of the option, but you'll get it on the first boot screen.

---

### Post by acer56 on 2006-07-04
What?? when i hold down c a black screen appears telling me to type live video=something and i press return it says loading then the ubuntu orange ubuntu progress bar appears and when that finishes a blue background with a flat grey window appears saying cannot find server x (your graphical interface) press yes to see digounise i click yes and a bunch of programing language appears which i dont under stand i click yes again and it takes me to that black screen with white writing telling me to type sudo to see admin commands.

---

### Post by Apple 101 on 2006-07-04
Try reconfiguring your xorg.conf file when it allows you to give *sudo* commands:  *sudo dpkg-reconfigure xserver-xorg*

---

