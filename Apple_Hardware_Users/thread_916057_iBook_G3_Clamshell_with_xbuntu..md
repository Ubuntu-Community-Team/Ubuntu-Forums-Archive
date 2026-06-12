---
title: "iBook G3 Clamshell with xbuntu."
date: 2008-09-10
forum: Apple Hardware Users
---

### Post by Nall on 2008-09-10
I'm trying to get Xubuntu on my older iBook G3 firewire editon. The installer goes through without a hitch. (I used the alternate CD, because some thread said to use that with the old ibooks). When the system boots up for the first time it gets to the login screen, but the screen is disjointed.  It seems like its at the wrong resolution, but the mouse will wrap from bottom to top.  It works seemingly, I just can't see the login prompt.

I saw this:

[https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz](https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz)

But now that I have xbuntu on it, is there some way to start in terminal instead of the GUI, or do I need to install Ubuntu to have a native terminal?  All of the xbuntu documentation tells you to start the terminal via a menu.  I can't do that if I can't see to log in, or the menu. Haha.

Not even sure if that will help, but its the best I could find.  Any help would be sweet.

~Thanks

---

### Post by pxwpxw on 2008-09-10
you can get terminal tty1  using keys
```

 control alt F1

```

you can start up in a root terminal from the yaboot  boot prompt by entering 
```

  linux single

```
(where linux is the menu option shown in the yaboot boot menu).

from the root terminal  you can disable the desktop startup step by disabling the
gdm link. (and noting how to restore it)
 - This one - where ** is some number like 20
```
 
/etc/rc2.d/ S**gdm 

```

---

### Post by Nall on 2008-09-11
Thanks much.  Just had to set the resolution lower, everything seems good now.

---

