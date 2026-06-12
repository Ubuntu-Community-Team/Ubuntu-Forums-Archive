---
title: "Screen Resolution"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by doradee on 2008-03-21
Hi. I am giving Ubuntu a try for the first time today. I installed it on an HP/Compaq nw8440 laptop. The problem is that I cannot get the screen resolution I want to work. When this same machine was running Windows XP, I had the resolution set to 1680x1050, which is what I want. On Ubuntu, none of the resolutions work except for 1280x1024 (the screen becomes completely messed up and unreadable when I tried to change). But the 1280x1024 resolution is not ideal because the monitor is a widescreen LCD- that resolution stretches the picture horizontally, and everything looks distorted.

I am very new to this. I have looked on this forum and on the internet for a fix, but I'm still lost as I'm not familiar with how Ubuntu works at all. Any help would be much appreciated. Thank you very much!

---

### Post by oedha on 2008-03-21
what display adapter do you have ?
what if you open terminal and type :==> sudo dpkg-reconfigure -phigh xserver-xorg
you can select the resolution there....
another one :==> sudo dpkg-reconfigure xserver-xorg

---

### Post by unutbu on 2008-03-21
When you say you've tried changing the resolution, do you mean you
Clicked System>Administration>Screens and Graphics?

---

### Post by oedha on 2008-03-21
no.....AFAIK...that can change the resolution which you have assigned before
to assign a new resolution you have to open terminal
applications - accesories - terminal
type my previous commands....:)

---

### Post by doradee on 2008-03-21
BRILLIANT! That worked like a charm. Thank you so much for such a prompt response.

---

