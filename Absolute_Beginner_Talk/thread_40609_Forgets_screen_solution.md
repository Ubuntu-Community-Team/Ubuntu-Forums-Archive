---
title: "Forgets screen solution"
date: 2005-06-09
forum: Absolute Beginner Talk
---

### Post by heltinde on 2005-06-09
Good evening

Today I got a strange problem; my computer seems to forget it's screen solution (went from 1024*786 to 640*480). I made a dpkg-reconfigure xserver-xorg, and it all seemed fine again - until reboot. I now have the same situation. What is going on?

I have an onboard Ati Rage Pro 4 MB.
Yesterday it was fine (it was a new installation, and Ubuntu made the decisions).

Lise

---

### Post by poofyhairguy on 2005-06-09
[QUOTE=heltinde]Good evening

Today I got a strange problem; my computer seems to forget it's screen solution (went from 1024*786 to 640*480). I made a dpkg-reconfigure xserver-xorg, and it all seemed fine again - until reboot. I now have the same situation. What is going on?

I have an onboard Ati Rage Pro 4 MB.
Yesterday it was fine (it was a new installation, and Ubuntu made the decisions).

Lise[/QUOTE]


Hmmm. What color bit depth do you use? I bet if you put in on 16bit it would say.

---

### Post by heltinde on 2005-06-10
OK did that, and for now it seems to work alright. But this is strange: I only chose 3 screen solutions when I reconfigured, but in Gnome I now have 8 options.

It makes me wonder: Do the reconfigure really overwrite the old file made automatically by Ubuntu? What are the names of those files, so I can check my self?

---

### Post by poofyhairguy on 2005-06-10
[QUOTE=heltinde]
It makes me wonder: Do the reconfigure really overwrite the old file made automatically by Ubuntu? What are the names of those files, so I can check my self?[/QUOTE]

to see the file it edits:

gksudo gedit /etc/X11/xorg.conf

---

### Post by heltinde on 2005-06-10
OK, checked it, and it lists the same options, as I chose under dpkg-reconfigure.

By the way; I saw 2 files:
1) xorg.conf and a lot of numbers (date and time on my last reconf).
2) xorg.conf

When I make a reconfigure (no. 1) is it then automatically copied to no. 2?

---

### Post by poofyhairguy on 2005-06-10
[QUOTE=heltinde]OK, checked it, and it lists the same options, as I chose under dpkg-reconfigure.

By the way; I saw 2 files:
1) xorg.conf and a lot of numbers (date and time on my last reconf).
2) xorg.conf

When I make a reconfigure (no. 1) is it then automatically copied to no. 2?[/QUOTE]

Yep. Thats its whole purpose.

---

### Post by heltinde on 2005-06-10
Thank's fellow with the funny hair ;-) You made me understand some basics I also can use in other situations.

---

