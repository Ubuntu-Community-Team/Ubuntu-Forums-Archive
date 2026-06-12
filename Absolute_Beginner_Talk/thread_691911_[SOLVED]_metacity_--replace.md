---
title: "[SOLVED] metacity --replace"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Xoanan on 2008-02-09
Hi All

I am trying to remove Compiz and go back to the old window manager.  I have seen the post of the code metacity --replace and I have tried that before I attempted to remove compiz and I got a response that the system has received a request from an outdated client with no timestamp. 

Could it have something to do with the compiz switch that I have installed?

```
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp

```

---

### Post by Xoanan on 2008-02-09
I tried something else I saw" compiz --replace and I got something more interesting

```
xoanan@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:01.0 0300: 8086:7125 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (1024): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 


```

In case anyone asks, I am using an i810e vid card

---

### Post by overdrank on 2008-02-09
HI and if you do not want to use compiz then just go to system, preference, appearance, visual tab and select none.

---

### Post by Xoanan on 2008-02-09
> **overdrank said:**
> HI and if you do not want to use compiz then just go to system, preference, appearance, visual tab and select none.

There is no such option under system. I have settings,  but that has no option like that either,  I am using Xubuntu.

---

### Post by overdrank on 2008-02-09
> **Xoanan said:**
> There is no such option under system. I have settings,  but that has no option like that either,  I am using Xubuntu.

Ok that makes a big difference, metacity --replace is for gnome and xubuntu uses xfce as the desktop environment. I am sorry I do not have a xfce system running at the moment.
Edit you may look at the compiz switch that should work
[http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)

---

### Post by Xoanan on 2008-02-09
> **overdrank said:**
> Ok that makes a big difference, metacity --replace is for gnome and xubuntu uses xfce as the desktop environment. I am sorry I do not have a xfce system running at the moment.
Edit you may look at the compiz switch that should work
[http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)

I have that already;  I was hoping to uninstall them both; thanx

Basically, I want to go back to the original window manager; the Switch doesn't do that quite.  I know this because when I attempt to go to window manager, it tells me that my current window manager unknown does not support this application.  Any ideas?

---

### Post by angry_johnnie on 2008-03-10
open a terminal and type this:

```
killall compiz && xfwm4 --replace & disown
```

I think that should do it.

---

