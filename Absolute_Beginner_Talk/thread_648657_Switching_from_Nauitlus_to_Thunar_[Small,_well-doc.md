---
title: "Switching from Nauitlus to Thunar [Small, well-documented problem]"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-12-23
Hello Everyone!

I'm having a rather small problem, yet annoying one. I'm working on switching from Nautilus to Thunar, using the guide at [http://psychocats.net/ubuntu/nonautilusplease](http://psychocats.net/ubuntu/nonautilusplease).

It's gone well so far, but I think I might have encountered a problem.

Desktop shortcuts seem to be linked to Nautilus, even though I've tried going to Properties -> Open with --> Thunar. I can't make the selection, demonstrated in the .ogg video attached.

[SIZE="3"]I've attached some photos to help show you what I mean.[/SIZE]

The desktop shortcuts I'm trying to open with Thunar:
[IMG]http://img153.imageshack.us/img153/7883/screenshotxf1.png[/IMG]

A picture of the Open-with dialog, which won't switch:
[IMG]http://img208.imageshack.us/img208/5727/screenshotwwwpropertiestb2.png[/IMG]

I have an .ogg attached so you can see the behavior I'm talking about.

Thanks for your help in advance!

---

### Post by shareMenaPeace on 2007-12-23
Not sure if this is much help but zou could have a look in 

open in terminal

gconfig-panel

and browse apps down to nautilus and maybe some setting there can help you :)

---

### Post by alecwh on 2007-12-23
> **shareMenaPeace said:**
> Not sure if this is much help but zou could have a look in 

open in terminal

gconfig-panel

and browse apps down to nautilus and maybe some setting there can help you :)

I don't see anything, and I think you mean gconf-editor. Thanks anyway though. Anybody have any ideas?

---

### Post by shareMenaPeace on 2007-12-23
oops, sorry yes i mean editor ...omg i better take a sleep :)

---

### Post by alecwh on 2007-12-23
Well, I haven't gotten an answer, but I found a work-around.

For each 'shortcut' I want to launch with Thunar, I actually DELETED the shortcut, and then added a new 'launcher' with the command being:

thunar 'path/to/directory'.

Simple enough. Hope this helps someone.

EDIT: An external hard drive/ipod/mp3 player/flash drive WILL OPEN IN NAUTILUS, for reasons not known to me. If you have a fix, please PM me.

---

