---
title: "Unbuntu + Other Desktop Environments"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-02-22
Here's my noobie question:
  
Are the two desktop environments totally independent (Ubuntu/Kubuntu)?  For example -- 
If I were to install Kubuntu alongside my Ubuntu installation, would I have to set up printer sharing and the various codecs for MP3 and DVD all over again?  Or does Kubuntu take these settings from what is already installed in Ubuntu?

Thanks!

---

### Post by Crakie on 2007-02-22
They are not totally independent... most settings will transfer from one environment to another.

---

### Post by louis_nichols on 2007-02-22
Everything is shared. If you install Ubuntu and then add the KDE environment, you won't have 2 OS's but one OS with 2 possible GUIs. Multimedia applications can use the same codecs (gstreamer is common snd used by both amarok and Rhythmbox, for example), the printer subsystem will be the same and drivers only one of each, only printing screens will look different. Your Firefox will look and behave the same in both environments.

This is actually a fundamental and very good part of Linux, that it is based on interdependencies between various pieces of software. This way, if an application (or rather, a library), does a task well, all apps that need to accomplish that task will use the library. So there is no space consuming redundancy and, instead of dividing efforts in re-inventing the wheel, a good library can be continously improved. This is not to say, though, that there is only one alternative for everything. In fact, there are many alternatives for pretty much every task.

---

### Post by Bachstelze on 2007-02-22
First off, Ubuntu and Kubuntu are *not* desktop environments. You're not completely mistaken thoiugh because tha major difference between them is that they install different desktop environments - Ubuntu installs Gnome, Kubuntu installs KDE.

To install KDE in Ubuntu, the most common way is

```
sudo aptitude install kubuntu-desktop
```

Except the Gnome -specific ones, all your settings will be saved, you can think of it as changing the painting of your car, the engine settings are not modified.

---

### Post by arkangel on 2007-02-22
Linux in that sense is a set of layers
the kernel  is the core of the system, over the kernel  run several things,  one is the X server (Xorg server ) which is responsible of the graphical stuff 

The X server doesn't take care of the menus or the window frames , for that there is what is called a windows manager (there are plenty of these),  these run over the Xserver .

Something that is more complete than a Windows manager is a desktop Environment. These consist of a Windows manager and integration features for opening files,  several  gui and programs for administration ,etc,etc , (KDE , gnome,Xfce and several commercial  ones ) 

you can have installed  several Desktops or none,  or simply only windows managers,  and tell the X server , "look, when using graphical stuff  load such or such window manager or desktop "   

[http://xwinman.org/]("http://xwinman.org/")

[http://en.wikipedia.org/wiki/Window_manager]("http://en.wikipedia.org/wiki/Window_manager")

here you will find a small reading  with more clarifications :)

---

### Post by chaplanger on 2007-02-22
If I understand correctly -- basic system settings (printer, codecs etc) will work in both Gnome and KDE environments. AND All of my installed programs will appear in both environments.
 
> **HymnToLife said:**
> 
Except the Gnome -specific ones, all your settings will be saved, you can think of it as changing the painting of your car, the engine settings are not modified.

If this is the case, what can I expect to have to duplicate in KDE?  Are we talking about applications that in the repositories begin with g(gnome?) as opposed to the "k" applications?

Thanks again for all your help!

---

### Post by Bachstelze on 2007-02-22
No. When a program is installed, it is installed regardless of the DE you run. It may not appear in the menus but you will still be able to run them from the terminal and add them to trhe menus if you wish. When I was speaking of "Gnome-specific" settings, i was thinking of e.g. your desktop wallpaper - the one you set in Gnome does not appear in KDE and *vice versa*.

---

### Post by chaplanger on 2007-02-22
> **HymnToLife said:**
> No. When a program is installed, it is installed regardless of the DE you run. It may not appear in the menus but you will still be able to run them from the terminal and add them to trhe menus if you wish. When I was speaking of "Gnome-specific" settings, i was thinking of e.g. your desktop wallpaper - the one you set in Gnome does not appear in KDE and *vice versa*.

Excellent!  Thanks so much

---

