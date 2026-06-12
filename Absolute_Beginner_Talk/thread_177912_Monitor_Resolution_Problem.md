---
title: "Monitor Resolution Problem"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by malkers on 2006-05-17
Hi,

Just installed ubuntu and the resolution will not go higher than 1024x768 :( 

Have tried some of the suggestions in changing the xorg.conf file in the modes [HowTo:change resolution]("http://ubuntuforums.org/showthread.php?t=83973")  etc but I can't find the vsync/hsync for my monitor 
(dell p1110) (it's a 21" flat screen CRT)

Also installed the nvidia proprietry drivers ](*,) 

Any suggestions?

---

### Post by malkers on 2006-05-17
After much tweaking I found I had to:

get the vsync and hsync, type them into xorg.conf
do "sudo /etc/init.d/gdm stop"
then "sudo /etc/init.d/gdm start"
not "startx"

duh.

---

