---
title: "really slow and a few other questions"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by thedevilisbad on 2007-04-12
I'm pretty new to ubuntu and finally got DSL so it's actually worth using it. When I installed 6.10 all the graphics along with the internet go extremely slow, this doesn't happen on th 7.04 beta live Cd (I can't install 7.04 but that is another story). What could cause this problem. Also how can I configure the GRUB bootloader so Windows automatically starts instead of ubuntu (this is a family PC and my parents use Windows). My 3rd question is of less importance, how do you edit ubuntu so the number lock automatically turns on?

Hope to be as good as you guys,

Aaron

---

### Post by PetePete on 2007-04-13
graphics could be going slow because you are using incorrect drivers.. post your xorg.conf and your video make/model.

internet MIGHT be going slow because of IPv6 (check some posts here for guides about firefox and ipv6 disabling)

you can configure grub by editing (with sudo) 

/boot/grub/menu.lst          
then look at the bottom, see what position windows is on the list, say its third below ubuntu and ubuntu recovery. then go up the file again to 

default            0

and change it to 
default    2 

(presuming that windows was the 3rd one down.... the count starts at 0 ;)  )

---

