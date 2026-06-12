---
title: "Problems installing vlc"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Europa7 on 2008-02-02
I just installed Ubuntu 7.1 and I'm having trouble installing any programs. I'm trying azureus, winamp, and vlc. I've tried with the terminal and with synaptic packet manager. For vlc trough the terminal I'm getting "the following packages have unmet dependencies" libavcodec1d, libavformatld etc. For vlc through synaptic packet mgr "can't be authenticated" warnings and "mark additional changes". I've even tried programs which are authenticated, like splashy, and I'm getting "could not mark all packages for  install or upgrade". All my third party and ubuntu software sources (except source code) are checked.

---

### Post by taurus on 2008-02-02
Sounds like your network connection wasn't working when the installer probed for it during the installing process.  Therefore, you either don't have any repos available in /etc/apt/sources.list or limited numbers.

Click System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and put a check mark in front of all the lines except the last one, Source code, and the Cdrom in the window below.  Close it and press Refresh.  Now, Search for vlc and install it from there.  If not, close down synaptic window and install it again from a terminal.

Otherwise, post the output of this command here from a terminal.

```
cat /etc/apt/sources.list
```

---

### Post by Europa7 on 2008-02-02
Thank you. I got it installed. Synaptic just needed to be refreshed/reloaded.

---

### Post by Europa7 on 2008-02-02
:guitar:

---

### Post by ninestar on 2008-04-05
Sound advice -- I had turned of my connection during installation because it always froze when 'checking mirrors' (perhaps I only needed to turn off the wireless detector ?) so that's why I missed out on repos. I know it's a bit belated, but I just found this after combing the internet for different methods of fixing many problems that wouldn't work because of this, thanks !

---

