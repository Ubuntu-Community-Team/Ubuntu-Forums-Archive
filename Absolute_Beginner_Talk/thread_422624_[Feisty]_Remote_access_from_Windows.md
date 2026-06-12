---
title: "[Feisty] Remote access from Windows"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Cypher on 2007-04-25
Greetings,

I'm an old hat at Linux, but a relative newbie with Ubuntu and more appropriately Upstart. I had a Fedora Core 5 based PC running KDE that I used VNCSERVER/VNCVIEWER to get access to. The PC would start up in multi-user (non-graphical) mode and I would SSH into the  box to run VNCSERVER and "startkde" to get my session running.

Before thinking of all the ramifications, I removed the Fedora Core 5 installation and replaced it with Feisty Fawn running GNOME. Everything works fine on PC itself, but I'm having one heck of a time getting my VNC functionality back.

I have tried the Remote Desktop option, but that just seems WAY too slow, and the fact that I have to be logged in isn't helping. I tried in vain to setup FreeNX yesterday and got things installed on the server, but couldn't get the client to behave.

I would much rather return to my old way of manually starting up VNCSERVER and a GNOME session through SSH and login through VNCVIEWER.

To that end, I have a couple of questions.
[LIST=1]
[*]How do I make Ubuntu start up in a text-console as opposed to the full GUI?
[*]What is the GNOME equivalent of "startkde" to get a new session running when GNOME isn't running at all?
[/LIST]
Regards

---

### Post by garlik42 on 2007-04-25
Here is some info on vnc server stuff
[https://help.ubuntu.com/community/VNCOverSSH?highlight=%28server%29%7C%28vnc%29](https://help.ubuntu.com/community/VNCOverSSH?highlight=%28server%29%7C%28vnc%29)

to start X, try "startx"

I don't know how to start in text mode, but my guess is it has something to do with disabling gdm or kdm from the startup.

---

### Post by Cypher on 2007-04-25
Thank you for that pointer, I needed to use tightvncserver and I now have things working as expected.

I found that I can use "gnome-session &" from within my ~/.vnc/xstartup to bring up the Gnome desktop which is very cool. However, I've found an issue that the keyboard mapping is messed up while GNOME is running. If i use the default values that tightvncserver uses which is just to start an XTERM, then the keyboard mapping is fine. With gnome, a->a, b->s, c->d and so on. 

Any thoughts?

---

### Post by garlik42 on 2007-04-25
That sounds very weird. It's not a dvroak mapping, I am not sure why that would happen.
I personally use vncserver and any key mapping issues I do have seem to be related to the client, I wonder if this might be the case for you ?

---

### Post by Cypher on 2007-04-25
Interestingly I installed KDE on there and when I use that through Tighvnc viewer, everything works as expected, no problem with keyboard mapping. Very strange..

I think I have it working enough now for what I need..

---

### Post by Bex_77 on 2007-07-09
Hi, I am also having the same key mapping issue under gnome and tightvnc, I tried to update vnc to the latest by installing the rpm package but then I have all sorts of font faults when trying to start a session

---

