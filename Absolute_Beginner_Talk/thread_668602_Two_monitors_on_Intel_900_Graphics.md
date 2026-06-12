---
title: "Two monitors on Intel 900 Graphics"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Valir on 2008-01-15
Hi,

So far I have figured out most things that I need for Ubuntu coming from XP. But I can't solve one thing. 

I want to plug an additional monitor with extended desktop. 

I have a Acer 4062LMi, with Intel Graphics Media accelarator 900 (the graphics card is 915 I remember from xp)

The gnome automatically found while installing ubuntu a driver called Intel experimental mode, however it does not accept an extra monitor, (it is grayed out)

When I try to change the graphics card, telling e.g. that it should find Intel 915, it chooses i810, the option to choose additional monitor opens, i log out, but ERROR the gnome does not start. 

I had to do dpkg-reconfigure xserver-xorg to be able to go back. 

So what am I doing wrong? Most things in Ubuntu are more clever than XP, but adding an additional monitor seems not to be so automatic.

best regards

---

### Post by overdrank on 2008-01-16
> **Valir said:**
> Hi,

So far I have figured out most things that I need for Ubuntu coming from XP. But I can't solve one thing. 

I want to plug an additional monitor with extended desktop. 

I have a Acer 4062LMi, with Intel Graphics Media accelarator 900 (the graphics card is 915 I remember from xp)

The gnome automatically found while installing ubuntu a driver called Intel experimental mode, however it does not accept an extra monitor, (it is grayed out)

When I try to change the graphics card, telling e.g. that it should find Intel 915, it chooses i810, the option to choose additional monitor opens, i log out, but ERROR the gnome does not start. 

I had to do dpkg-reconfigure xserver-xorg to be able to go back. 

So what am I doing wrong? Most things in Ubuntu are more clever than XP, but adding an additional monitor seems not to be so automatic.

best regards

HI and welcome, maybe this link will help
[http://thinkwiki.org/wiki/Installing_Ubuntu_6.06.1_on_a_ThinkPad_R60e#Using_xrandr_with_Ubuntu_7.10](http://thinkwiki.org/wiki/Installing_Ubuntu_6.06.1_on_a_ThinkPad_R60e#Using_xrandr_with_Ubuntu_7.10)
good luck!

---

### Post by Valir on 2008-01-16
Hi thanks for the tip,

It helped me understand that there is a problem with i810 in ubuntu 7.10, but I couldn't figure out what applies to me. I have a CRT 17'' monitor on the left side of my laptop, and want to extend the desktop to the left. 

I'v noticed that when I plug in the monitor on startup Ubuntu treats the external monitor as the main monitor, which is what was in the wiki. 

I use normal resolution so I am not sure what i should pick?

Sorry a n00b here in these matters.

---

