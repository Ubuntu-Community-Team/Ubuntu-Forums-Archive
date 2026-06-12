---
title: "Will too many environments crash?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-20
I have Gnome, KDE4, IceWM and XFCE.. Im planning for more, or you might say, everything !!!
If I install more, will it affect the stability of the system?
If no, then please advise which environments should I try?..

---

### Post by p_quarles on 2008-03-20
No, it won't affect the stability of the system. You only run one of them at a time.

---

### Post by jordanmthomas on 2008-03-20
No, you can have as many installed as you feel like.
I highly recommend openbox and if you are in the mood for editing configuration files for a while, awesome window manager is...errr...awesome.

---

### Post by sayakb on 2008-03-20
Downloading openbox :D
Plus, I have a peculiar problem. I once installed KDE4 alpha, until I got the stable one. I "upgraded" to the stable one. Now, I find that package KDE4 is not installed and I cannot install any KDE4 app (It says: Depends on dolphin-kde4, but it is not going to be installed. Yes, a few apps are installed though, and KDE4 runs fine, just that it has no apps.. what do I do?

---

### Post by sayakb on 2008-03-20
Openbox doesn't seem to work. I get two options: openbox and openbox-kde at the login prompt. When I log in to openbox, the screen becomes black and freezes. If I select openbox-kde, it tells me that "Your session lasted less than 10 seconds. If you did not log out, it could be an installation problem or you are running out of space". I have 20GB free on my HDD. Plus, these are the packages I installed:

```
sudo apt-get install openbox openbox-themes pypanel obconf stalonetray
```

---

### Post by jordanmthomas on 2008-03-20
Try running obconf in another session first.
You probably don't have a configuration file for it.

Edit:
Are you sure it's frozen?  Try right clicking the desktop.

---

### Post by sayakb on 2008-03-20
WHOA!!!! It wasn't actually frozen!! ):P 
I get terminal editor and obconf when I right click!! :D
Is there no file manager?

Edit: I can run obconf pretty well.. just seems like I am too dumb :(

---

### Post by p_quarles on 2008-03-20
> **LinuxIsInnovation said:**
> WHOA!!!! It wasn't actually frozen!! ):P 
I get terminal editor and obconf when I right click!! :D
Is there no file manager?
No, no file manager. Openbox is simply a window manager, and does not provide any of the functions of a desktop environment. You get to build that for yourself.

Any file manager you like (konqueror, dolphin, thunar, nautilus, rox-filer, midnight-commander) will do.

---

### Post by sayakb on 2008-03-20
> **p_quarles said:**
> No, no file manager. Openbox is simply a window manager, and does not provide any of the functions of a desktop environment. You get to build that for yourself.

Build it, as in, make my own, or just use some other session's?? If it meant make my own, then where should I start? (I am not much of a developer you see :/)

---

### Post by p_quarles on 2008-03-20
> **LinuxIsInnovation said:**
> Build it, as in, make my own, or just use some other session's?? If it meant make my own, then where should I start? (I am not much of a developer you see :/)
You don't have to develop anything, you just need to select the components you want to use in your Openbox session. 

This might help:
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by sayakb on 2008-03-20
The guide seems really helpful. Thank you :)

---

