---
title: "trying to get xgl up and running"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-18
followed a guide for installing the ati fglrx drivers which are installed but when trying to install xgl it says to change the following line in the xorg.conf file when i do my computer no longer boots. I have to go into debug mode then manually edit the xorg file back to what it was.

Under Section "Screen" The Identifier line needs to be changed to:

     Identifier "aticonfig-Screen[0]" 

it's was Default Screen

it's radeon 9600 agp card using the hdmvi output

---

### Post by Anduu on 2006-06-18
If you are using gnome try this guide [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

It is very comprehensive and is on a forum dedicated to XGL.

Worked flawelessly for me.

---

### Post by lime4x4 on 2006-06-18
thanks that worked flawless

---

### Post by lime4x4 on 2006-06-18
were can i find different addons and such..I'm looking for the rotating desktop addon

---

### Post by lime4x4 on 2006-06-18
meant where would i find info on enabling the rotating desktop

---

### Post by Anduu on 2006-06-18
All the features should be installed and enabled automagically....possibly you arent using the right shortcuts.

ctrl+alt+leftclick/drag rotates the desktop.

Are you sure it is working?Easiest way to tell is if your windows wobble when you drag them around.

---

### Post by lime4x4 on 2006-06-18
yeap that worked thanks...

---

### Post by Anduu on 2006-06-18
Sweet :D 

I wish I had found that How-To when I first tried to install XGL...what a nightmare for an Ubuntu newb like I was :p

---

