---
title: "loading up GUI"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by adamhhh on 2005-12-06
ok im completely new to ubuntu, its installed but it only loads up the command line on start up- how do i get onto the graphical operating system?

---

### Post by Mr. Electric Wizard on 2005-12-06
First off what video card are you using, ATI?
If so, that is what happened to me until I found this thread:

[http://www.ubuntuforums.org/showthread.php?t=76116&highlight=ati+200m]("http://www.ubuntuforums.org/showthread.php?t=76116&highlight=ati+200m")

Might help...

---

### Post by raublekick on 2005-12-06
What happens if you type
```
startx
```
If nothing happens, or it gives an error, you probably did the server install.

To get the Gnome, etc... type
```
sudo apt-get install ubuntu-desktop
```
If you didn't have this installed, it will install everything you need and get you up to a normal Ubuntu install. If this isn't the problem it will just tell you that nothing needs done, so we can move on to another solution.

---

### Post by teaker1s on 2005-12-06
try this written by me edited by sam 
[https://wiki.ubuntu.com/CommonProblemsGraphics?highlight=%28problems%29%7C%28common%29](https://wiki.ubuntu.com/CommonProblemsGraphics?highlight=%28problems%29%7C%28common%29)

---

