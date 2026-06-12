---
title: "I think I messed up my linux"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Stabilityonitsown on 2008-04-04
Hi guys, before we start I just want to say im using debian.

Anyways so ever since I got linux I have been download programs and running the configure script and the install script that was in those files, but what I have been noticing is all of those programs I downloaded I don't see in my menu ANYWHERE! So now I am thinkingm I just have a bunch of cluttered useless files created all over my computer. Since I have no clue on how to install stuff so I do the retarded thing and run random scripts to see if it installs, and it didn't work out that well. Another thing is I have been install programs through apt-get and none of those showed up in the menu even if I followed the tutorial right! Please help me as I MAY need to reinstall debian!!

---

### Post by TheLions on 2008-04-04
does that installed files show in Synaptec?

if it does you can run it simply by pressing Alt+F2 and type the name of program...

---

### Post by kellemes on 2008-04-04
> **Stabilityonitsown said:**
> Hi guys, before we start I just want to say im using debian.

Anyways so ever since I got linux I have been download programs and running the configure script and the install script that was in those files, but what I have been noticing is all of those programs I downloaded I don't see in my menu ANYWHERE! So now I am thinkingm I just have a bunch of cluttered useless files created all over my computer. Since I have no clue on how to install stuff so I do the retarded thing and run random scripts to see if it installs, and it didn't work out that well. Another thing is I have been install programs through apt-get and none of those showed up in the menu even if I followed the tutorial right! Please help me as I MAY need to reinstall debian!!

You need to give a specific example..
If you install "geany" for example, like so..
```
sudo apt-get install geany
```
It doesn't show up in the menu's?

---

### Post by Stabilityonitsown on 2008-04-04
Well I install small things like wine, python, moblock, and none show in the menu. BTW I used apt-get and another thing is I just got 1 program to show in the menu without having to add it manualy, its Python IDLE got it from package manager.

---

### Post by kellemes on 2008-04-04
> **Stabilityonitsown said:**
> Well I install small things like wine, python, moblock, and none show in the menu. BTW I used apt-get and another thing is I just got 1 program to show in the menu without having to add it manualy, its Python IDLE got it from package manager.

Python is no more then a development platform, it's not an application you run.
Moblock is a console application you need to run from terminal.
Wine should create a menu entry but you can also run the gui from terminal like so.. "winecfg"

---

### Post by Stabilityonitsown on 2008-04-04
Actually python is a programming language that is already installed on your machine, but you need an IDLE to use it to make programs.

---

