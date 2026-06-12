---
title: "Xubuntu Boot Screen"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by brady618 on 2006-05-12
I know this is kind of anal, but how do I set it up so there is the xubuntu load screen instead of the kubuntu one?  I have xcfe, kde, and gnome and use xcfe almost exclusively.  I really hate the way the kubuntu one looks.  Is there some way to set it up to do this?

---

### Post by testube_babies on 2006-05-12
Have you tried installing the "xubuntu-artwork-usplash" package?  Maybe with that you should also uninstall "kubuntu-artwork-usplash."  I'm not sure this would work, but it's my best guess.

---

### Post by brady618 on 2006-05-12
I have multiple splash screens available in xubuntu.  Will installing  "xubuntu-artwork-usplash" allow for more screens?  Will that affect the bootscreen?  I'm not sure there's an option to change the bootscreen in the display manager.  Btw, I like yer signature testtube :D

---

### Post by brady618 on 2006-05-12
OK, I uninstalled the Kubuntu usplash, reinstalled the xubuntu one, and nothing.  Then I uninstalled the kubuntu desktop - nothing.  then I uninstalled Kubuntu -still nothing.  Perhaps I didn't entirely uninstall Kubuntu?  It only freed like 200 kb, and the bootscreen and login screen are still both Kubuntu, and it gives me an option to open a kde session still.  Did I uninstall it incorrectly?  What would the normal command be for uninstalling?  I used sudo aptitude remove xubuntu-desktop.  Any help would be greatly apprectiated.  All I want is an Xubuntu bootscreen, is that so much to ask!! ;)

---

### Post by brady618 on 2006-05-12
I'm playing around, and I tried sudo dpkg-reconfigure xdm nad it said 
Package `xdm' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xdm is not installed

Is xdm not xubuntu?  I know kdm is kubuntu and gdm is ubuntu.  (is it possible that I just don't have the bott for xubuntu installed??)

---

### Post by adssse on 2006-05-12
Have you tried trying to apt-get xdm? I am not sure if the manager is installed with the desktop.

---

### Post by blair on 2006-05-14
I'm having a similar problem. Trying to get an xdm login screen or a Xubuntu login screen and having no luck. 

In answer to your question, xdm is a generic display manager provided by X, it is not a Xubuntu display manager. Completely different animals. In fact I'm not aware of any Xubuntu-specific display manager, which is why I'm trying to get a simple xdm going. I have it installed but it does not auto-load on boot up. 

Also, I went to install xubuntu-artwork-usplash and apt indicated it is already installed, therefore it must have been installed when I installed the xubuntu-desktop package.

Any suggestions appreciated. thanks.

---

### Post by linuxa on 2006-05-27
I don't have any other desktop manager installed on this computer, so I can't try it myself today. See if you can change the app pointed to in:

/etc/X11/default-display-manager

to something like gdm or xcfe?

---

### Post by sinkxdie on 2006-05-27
I think you did

apt-get install kubuntu-desktop

instead of aptitude, so your going to have some hard uninstall problems to uninstall kubuntu.

---

### Post by confused57 on 2006-05-27
To completely uninstall Kubuntu-desktop if you installed with apt-get:

[http://www.ubuntuforums.org/showthread.php?t=96048&highlight=uninstall+kubuntu-desktop](http://www.ubuntuforums.org/showthread.php?t=96048&highlight=uninstall+kubuntu-desktop)

---

