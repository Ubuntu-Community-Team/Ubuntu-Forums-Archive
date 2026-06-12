---
title: "Debian Menu Help"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by sethdotcom on 2007-05-12
I installed Debian Menu through AutoMATRIX

But i don't see it, it says it can be found under applications but it is not there!
any advice?

---

### Post by oilchangeguy on 2007-05-12
you may have to go to applications, accessories, alacarte menu editor. and add it from there.
also have you looked in all of the listings under applications?

---

### Post by greysave on 2007-05-14
I am having the same problem.  When I attempt to click the visible check box nothing happens.  How do I set it up manually?

---

### Post by 67GTA on 2007-05-14
gksudo dpkg-reconfigure menu 
gksudo dpkg-reconfigure menu-xdg 
reboot

That should make it show up.
(I think it is some sort of bug)

---

### Post by greysave on 2007-05-14
What exactly are those commands doing?

---

### Post by 67GTA on 2007-05-14
The short version: (menu)updating the Gnome menu to include the Debian menu and(xdg)updating the Debian menu to include all of the installed apps.

---

### Post by greysave on 2007-05-15
> **67GTA said:**
> gksudo dpkg-reconfigure menu 
gksudo dpkg-reconfigure menu-xdg 
reboot

That should make it show up.
(I think it is some sort of bug)

This still did not work for me.  When I attempt to add the menu it does not allow me to check the visible check box.  Its as if Its not truely installed or it does not know where to go.

---

### Post by coady on 2007-05-15
Hi, I tried running> gksudo dpkg-reconfigure menu
gksudo dpkg-reconfigure menu-xdg but I get the following error> Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: menu is not installed.
I added 'menu-xdg' with```
apt-get install menu-xdg
```before running the commands above. Does anyone know what the 'dpkg-reconfigure' problem is? I would also like to have access to the 'debian menu'. Is this a bug in Feisty? Thanks. :) 
coady

---

### Post by coady on 2007-05-15
OK, on my previous error message...> but I get the following error
Quote:
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: menu is not installed.I forgot to add 'menu' along with 'menu-xdg'. After running```
sudo apt-get install menu
```I then ran```
sudo dpkg-reconfigure menu
sudo dpkg-reconfigure menu-xdg
```and rebooted. The problem is solved, and the 'debian menu' is reconfigured and appears under 'Applications' :) 
coady

---

### Post by stevejesus on 2007-11-07
Note, this doesn't require a reboot.  This doesn't require any reconfiguring of packages either.  Simply install menu-xdg, then do the following from a terminal, or Alt+f2 for a quick command;

killall gnome-panel

---

### Post by Ilmater on 2008-01-25
> **stevejesus said:**
> Note, this doesn't require a reboot.  This doesn't require any reconfiguring of packages either.  Simply install menu-xdg, then do the following from a terminal, or Alt+f2 for a quick command;

killall gnome-panel

It worked instantly... thanks for the advice!!!

---

### Post by jhenager on 2008-02-04
Worked perfectly. Thanks.

---

### Post by Hatchetfish on 2008-02-11
The reconfigures are helpful in one situation though; having installed menu and menu-xdg some time in the past, and later having the debian menu entry disappear (after it functioned/was present for some time) is usually fixed by the reconfigures and a reboot or restarting the gnome panel.

killall gnome-panel is much quicker than rebooting, whatever the reason to update an applet (which the menu is).  It can occasionally cause problems with applets though, and sometimes gnome-panel will refuse to start again, claiming there's another instance running already.

---

