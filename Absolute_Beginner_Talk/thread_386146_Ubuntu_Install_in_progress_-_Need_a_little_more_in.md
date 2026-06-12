---
title: "Ubuntu Install in progress - Need a little more info."
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Stormweaver on 2007-03-16
Hey gang,

Alright, the server is installed and running smooth from what I can tell.

However - Following advice about desktop I entered the following at prompt:

sudo apt-get install ubuntu-desktop


Now.. It looked all good till it started asking for a copy of the edgy disk, which I don't have.  Also want to make sure the desktop being installed is 64 bit.  So what do I need to do here?? I was under the impression it could pull down from the web what it needed.  Warned ya I was new! :)

Stormweaver

---

### Post by steve101101 on 2007-03-16
if you just want a graphical desktop you should grab the ISO file from [www.ubuntu.com](www.ubuntu.com) (there one for 64 bit machines)

this is also the cd that it is asking for the installation.

---

### Post by steve101101 on 2007-03-16
if you need more help/info just send me a private message.

---

### Post by annda on 2007-03-16
i think it's not desktop that you want to have the 64bit version of, but the kernel. the alternate install cd has that.

your software sources are in /etc/apt/sources.list if you don't have the cd, you will need to remove it as a source. i don't have a cd included there so i can't tell you exactly what line to delete - look at the file and get rid of the appropriate line(s).

---

### Post by steve101101 on 2007-03-16
if you haven't done too much work in ubuntu you can just reinstall it.

---

