---
title: "Can't Browse Root Directory"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by mengd2002 on 2006-11-07
Can anyone help me with this?  I'm running Ubuntu 6.10 and I can no longer browse the root "/" directory.  When I open Nautilus, "browse your computer icon", and double click on Filesystem, all I see is the Home and media folders.  It won't let me go anywhere else.  And yet it used to.  I noticed this after I installed the Kubuntu desktop.  Don't know if that has anything to do with it.  Thanks,
Don

---

### Post by taurus on 2006-11-07
It's probably permission thing.  Open a terminal and type

```
gksudo nautilus
```
Now, can you move to /?

---

### Post by mengd2002 on 2006-11-07
> **taurus said:**
> It's probably permission thing.  Open a terminal and type

```
gksudo nautilus
```
Now, can you move to /?

gksudo didn't do it.  I still couldn't get to the root "/" directory.  Any other ideas short of activating the root account so I can do stuff outside my home directory.  Thanks.

---

### Post by taurus on 2006-11-07
Open a terminal, Applications -> Accessories -> Terminal, and post the output of this command.

```
sudo ls -la /
```
And exactly what do you want to do outside of your $HOME directory?

---

### Post by jordanmthomas on 2006-11-07
Same thing happened to me when I switched to Gnome 2.16
You can still access everything, but you have to got to the folder directly.  For example, if you want to go into /usr, you have to press Ctrl - L and type /usr
It really was an annoyance.

---

### Post by JediCowboy on 2007-01-06
The exact thing has happened to me in the same way.  I installed kubuntu-desktop along with Ubuntu Edgy and now Nautilus will only show me my Home and Media folders when I try to browse to the / folder by clicking.  I can bring up any folder in Nautilus if I type it, /etc, for example, in the location bar, but I can't get there by clicking.  It's rather annoying.

Interestingly, I also installed Xubuntu at the same time I installed Kubuntu and the Thunar manager will let me click and browse as Nautilus used to.

Has a fix for this been found and posted in another thread I just haven't come across yet?

---

### Post by JediCowboy on 2007-01-06
Of course a few moments after I post I find the answer

[http://ubuntuforums.org/showthread.php?t=289565&highlight=nautilus+root+browse](http://ubuntuforums.org/showthread.php?t=289565&highlight=nautilus+root+browse)

---

