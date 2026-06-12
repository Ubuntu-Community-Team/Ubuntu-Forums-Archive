---
title: "I want to switch my computer from Kubuntu to Ubuntu."
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-12-13
I installed Kubuntu on my PC in my family room, but Ubuntu seems to be the preferred version *buntu. I recall that there's some simple command I can issue to have the entire thing swapped, but I can't remember what it is. 

Also, when I do switch, what will be lost and what will be kept?

---

### Post by meng on 2006-12-13
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
You'll need the longer apt-get remove command to purge KDE.
You'll lose the KDE-specific applications, e.g. amarok. If you want some of them back, you can install and run these in GNOME.

after you've purged KDE, simply:
sudo aptitude install ubuntu-desktop

---

### Post by Amablue on 2006-12-13
Another question:

My dad is doing work on the computer right now since he's on sick leave. How long will this whole process take? I don't want to tie up the computer unless I know he's not going to be needing it.

---

### Post by real_ate on 2006-12-13
well the process should only take about an hour to an hour and a half... but always leave about 5 for something going wrong :) 

also i would like to put forward a suggestion but i'm not sure if i know fully what i'm talking about here so any experts feel free to correct me.... why don't you just install the gnome desktop and run that session (or make gnome your default session) when you log in? that way you don't need to worry about things not working and you can purge KDE later... plus it drops your install time to 10 mins! or 15 if you want a cuppa tea ;)

---

### Post by meng on 2006-12-13
> **Amablue said:**
> Another question:

My dad is doing work on the computer right now since he's on sick leave. How long will this whole process take? I don't want to tie up the computer unless I know he's not going to be needing it.
If you want to play it safe, leave the computer on overnight and do it then. That should cover you even if your modem connection is slow.

---

