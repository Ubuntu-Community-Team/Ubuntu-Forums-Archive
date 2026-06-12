---
title: "X11 cannot be accessed from terminal"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by fritz3000g on 2008-02-07
I've been having graphics problems with an Intel laptop chipset, and a lot of the fixes have to do with modifying xorg.conf in the X11 directory.  However, my terminal doesn't let me go into X11.  It says that this directory doesn't exist.  I can go in any other directory I want to and modify things, but for some reason this one doesn't let me in.

Any ideas?

---

### Post by emarkd on 2008-02-07
1.  Are you sure you're capitalizing the 'X'?  Linux is case-sensitive.

2.  X11 is not in the root.  It's under /etc, so the full path would be /etc/X11.  Is that what you're using?

3.  You'll have to use sudo to edit the file, if you get that far

This is an important file and you should make a backup copy before you edit it.

---

### Post by kizmet_x on 2008-02-07
You can do it the graphical way. First find the file in the filesystem, then go to the terminal and type in

gksudo nautilus

Then navigate to that file and change it that way.

---

### Post by emarkd on 2008-02-07
> **kizmet_x said:**
> You can do it the graphical way. First find the file in the filesystem, then go to the terminal and type in

gksudo nautilus

Then navigate to that file and change it that way.

While this will work, please be very careful with that root Nautilus session.  One small mis-click or hitting <del> while you've got the wrong directory highlighted could be disastrous.  Be very careful.

---

### Post by peterbrewer on 2008-02-07
To edit your config file you could run one of the following:

from the command line outside of a gui:
> sudo nano /etc/X11/xorg.conf

from the command line in Ubuntu:
> sudo gedit /etc/X11/xorg.conf

from the command line in Kubuntu
> sudo kate /etc/X11/xorg.conf

Hope that helps.

---

### Post by jordanmthomas on 2008-02-07
```
sudo gedit .....
```
It's worth saying that you should use **gksudo** to launch graphical applications, so you don't mess up the permissions on your .ICEAuthority file or your .dmrc file.

For kde, the equivalent program is **kdesu**
So,
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by emarkd on 2008-02-07
> **jordanmthomas said:**
> It's worth saying that you should use **gksudo** to launch graphical applications, so you don't mess up the permissions on your .ICEAuthority file or your .dmrc file.


Not trying to hijack this thread, but I've been using sudo to launch graphical programs for years and have never heard this before or had a problem from it.  I checked both of those files on my system and they both have 600 permissions, but I don't even know what they do.   I tried a google search and couldn't find any more information.  Do you have a link to a resource where I can learn more about this?

---

### Post by jordanmthomas on 2008-02-07
[http://www.mail-archive.com/arch@archlinux.org/msg04963.html](http://www.mail-archive.com/arch@archlinux.org/msg04963.html)
Generally, it happens when you launch a KDE program from Gnome or vice-versa, but it's a good practice to get used to always just use gksudo so you don't have to worry about it.

Also, I think your ~/.dmrc file should actually have 644 permissions.

This all happens because sometimes sudo will use root permissions, but the user's configuration file.  It creates files that are owned by root sometimes (but not all the time) so it's kind of a crapshoot.

Try it with firefox, for example.  
```
sudo firefox
``` will use the user's config, but
```
gksudo firefox
``` will use root's (preferred, as to protect permissions)

Ah, found it: a brief discussion of the matter.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by emarkd on 2008-02-07
Thanks for the info.  I learned something new today :)

---

### Post by macogw on 2008-02-07
> **peterbrewer said:**
> To edit your config file you could run one of the following:

from the command line outside of a gui:
```

sudo nano /etc/X11/xorg.conf
```
from the command line in Ubuntu:
```

sudo gedit /etc/X11/xorg.conf
```
from the command line in Kubuntu
```

sudo kate /etc/X11/xorg.conf
```
Hope that helps..

If you use nano, the lines at the bottom tell you how to do stuff.  WriteOut means "save" and the ^ next to the letters means you hit Ctrl with that letter to do the thing written next to it.

---

