---
title: "Gnome fallng down"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by bellzii on 2007-07-02
Will i was doing some work i found that applications are opening very slowly, i rebooted and , i got that message saying that theres something wrong with gnome daemon and that some features like background ,themes...etc will not work and that next time daemon will try to reload...
since its been taking a long time than usual to open any application, could that be somekind of virus i got from a flash memory(which ive been using) or what is it?

is there a way of restoring ubuntu as it was before?

im using a ubuntu 6.10

thanks in advance

---

### Post by cogadh on 2007-07-02
There is almost no way it could be a virus, there have only been 14 Linux viruses since 1991 and none are currently in the wild. The odds that you have a virus affecting the operation of Gnome are slim to none.

It sounds like GDM failed to launch properly. Do a CTRL-ALT-F1 to close out of the window manager, log back in to the terminal and run this:
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```
that will stop and restart the GDM daemon. You should be able to log back in to the GUI normally.

---

### Post by bellzii on 2007-07-02
should i change to KDE ..or what ? what can i do?

---

### Post by cogadh on 2007-07-02
Sorry, I clicked the "Post" button before I finished typing by accident, just edited the original post with a suggestion.

---

### Post by bellzii on 2007-07-02
Is there a way i could reinstall ubuntu without loosing my saved packages and files

---

### Post by cogadh on 2007-07-02
You could reinstall just the desktop packages:
```
sudo apt-get install --reinstall ubuntu-desktop
```
However, I'm not sure what you have already installed in addition to the Ubuntu defaults, so I can't say for sure if that will affect anything you have added to your system.

Alternatively, if you created a separate partition for /home when you first installed, you can reinstall the entire OS without touching that directory.

---

### Post by bellzii on 2007-07-02
what i really need to keep is some packages i had to download and build for a project named gnuradio..its in the /home directory and unfortunately all ubuntu is on one drive

---

### Post by cogadh on 2007-07-02
I don't know anything about gnuradio, so I don't know if reinstalling the desktop packages will affect it.

Did you try the GDM stop/start suggestion I originally posted?

---

### Post by avik on 2007-07-02
cogadh's suggestion won't destroy anything.  It'll just reinstall gnome and the other packages that come with Ubuntu.

Also, having /home on another drive is always a good idea, whether or not you want to reinstall something.  Check out [ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/").

---

