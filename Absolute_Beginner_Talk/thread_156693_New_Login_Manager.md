---
title: "New Login Manager"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by Sonlc on 2006-04-07
Hi, just a quick question.  I want to install a new login manager.  This one [here](http://art.ubuntu.com/themes/gdm_greeter/1).  Can anyone tell me how I can do that?  Thanks alot!

---

### Post by KingBahamut on 2006-04-07
System > Administration > Login 

You should find what you need in there to install a new GDM theme.

---

### Post by aysiu on 2006-04-07
[QUOTE=Sonlc]Hi, just a quick question.  I want to install a new login manager.  This one [here](http://art.ubuntu.com/themes/gdm_greeter/1).  Can anyone tell me how I can do that?  Thanks alot![/QUOTE] That's the default for Kubuntu. Are you currently using Ubuntu? You may have to do this: ```
sudo apt-get update
sudo apt-get install kdm
```

---

### Post by Sonlc on 2006-04-07
Oh,  thanks.  What will that command do though?

---

### Post by aysiu on 2006-04-07
[QUOTE=Sonlc]Oh,  thanks.  What will that command do though?[/QUOTE] If you're using Ubuntu, your desktop environment is Gnome and your display manager is GDM. The display manager controls the login screen and themes.

If you *sudo apt-get install kdm*, you'll be using KDE's display manager: KDM. The theme you linked to is a KDM theme, not a GDM theme.

For the most part, GDM and KDM are pretty much the same. Here are some main differences, though:

1. If you have GDM installed, you won't be able to shut down from KDE. You'll have to log out and shut down from the login menu. Same applies to KDM and Gnome.

2. GDM themes can be installed by going to System > Administration > Login Screen Setup and dragging and clicking "install new theme" and selecting the .tar.gz.

3. KDM themes are usually installed by unzipping the .tar.gz, copying the unzipped folder to a particular other folder and editing a configuration file to point to that folder.

**Edit**: If you ask me, instead of installing KDM, you're better off just finding a GDM theme you like and installing that. You can find a whole bunch right [here](http://www.gnome-look.org/index.php?xcontentmode=150).

---

### Post by Sonlc on 2006-04-07
excellent advice aysiu, thanks alot!

---

### Post by appdx on 2006-04-12
err, I went to the themes thing and it wouldn't let me drag the tar.gz I wanted to use into it...and when I went to Install theme and browsed to my desktop it wasn't there, so I assume that it doesn't see as the right file type....help?

---

