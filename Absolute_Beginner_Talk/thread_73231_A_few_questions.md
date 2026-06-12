---
title: "A few questions"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by Pajj on 2005-10-08
I just installed Ubuntu last night and I've got a few questions. First, I can't find where all the applications are stored that come with it. I don't really understand how everything is laid out. What I'd like to do currently is install more fonts (I want my Verdana :( ) and I'm also curious if any of my plugins I used on Windows would work for xchat, specifically the xtray plugin which would give you a popup when someone says your name with their message.

Also, are there any security issues I need to worry about? I believe I have all the current updates but I'm wondering if there's anything I need to worry about.

---

### Post by dasunst3r on 2005-10-08
I would highly recommend [www.ubuntuguide.org](www.ubuntuguide.org) -- that will help you get the things you need.

---

### Post by Gustav on 2005-10-09
[QUOTE=Pajj]I just installed Ubuntu last night and I've got a few questions. First, I can't find where all the applications are stored that come with it. I don't really understand how everything is laid out. What I'd like to do currently is install more fonts (I want my Verdana :( ) and I'm also curious if any of my plugins I used on Windows would work for xchat, specifically the xtray plugin which would give you a popup when someone says your name with their message.

Also, are there any security issues I need to worry about? I believe I have all the current updates but I'm wondering if there's anything I need to worry about.[/QUOTE]
For verdana you can install msttcorefonts, type

sudo apt-get install msttcorefonts

in the terminal

Most applications are stored in the /usr/share/ directory. But there's no need to know that since they can all be started with their name. To start gimp you simply type

gimp

in the terminal (Or you find gimp in your menus. Most programs can be found in the menus.)

To install programs you can use the apt-get command or, more easely, use the synaptic package manager.

---

