---
title: "dual boot partition question"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by iheartpreggos on 2007-02-14
I am in the process of setting up a dual boot system with windows xp and ubuntu i have all of my partitions made but am a little confused when it comes to the "prepare mount points"

i have the following setup:

a 40 gig hd with a  20 gig partition where windows is installed
a 5 gig partition to install ubuntu 
a 1 gig partition for the swap
and a 14 gig partition for ubuntu "home"

now my question is how do i set up the mounting points.?

---

### Post by iheartpreggos on 2007-02-14
> **iheartpreggos said:**
> I am in the process of setting up a dual boot system with windows xp and ubuntu i have all of my partitions made but am a little confused when it comes to the "prepare mount points"

i have the following setup:

a 40 gig hd with a  20 gig partition where windows is installed
a 5 gig partition to install ubuntu 
a 1 gig partition for the swap
and a 14 gig partition for ubuntu "home"

now my question is how do i set up the mounting points.?

i forgot to mension i also have a 200gig drive but that is for windows media

---

### Post by soham on 2007-02-14
use gparted and it will get grub
like /boot/swap

---

### Post by mikewhatever on 2007-02-14
Windows partition: /media/hda1
Ubuntu root:          /
Ubuntu swap:         swap
Ubuntu home:        /home

If you are installing on a SATA HD,then change hda1 to sda1.

Good Luck.

---

