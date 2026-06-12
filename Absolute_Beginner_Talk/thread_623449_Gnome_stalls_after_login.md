---
title: "Gnome stalls after login"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by siege911 on 2007-11-25
So I recently had a weird issue with my computer.

I have a fresh install with Gutsy. Then installed the "Perfect Server Setup -Gutsy" however I do have Gnome so it's not a pure server setup. I also have "nomachine" installed so I can access my desktop from elsewhere.

It has been working great. Then all of a sudden, I can get to the login screen and put in my credentials. It goes to the pure brown screen and stalls there forever. I can hit Ctrl Alt Backspace and go back to the login screen and try again to no avail. Then it briefly worked last week and it's back to the same stall.

I can however login via the nx client on a Windows machine. Gnome comes up fine and everything.

I don't know linux enough to figure out how to trouble shoot this or what is stalling it.

Where do I go from here?

---

### Post by jfinkels on 2007-11-26
Can you start X from the virtual terminal? Once you see the login screen, press <Ctrl>+<Alt>+<F1>, login, and type:```
sudo /etc/init.d/gdm stop
``` and then type:```
startx
```

Is there any error output? Have you recently installed or reinstalled drivers for your video card? What is the contents of your "/etc/X11/xorg.conf" file? Your xorg.conf is the configuration file for the X server  (the graphical windowing system).

If you can't figure anything out, you may try reconfiguring your X server by doing:```
sudo dpkg-reconfigure xserver-xorg -phigh
``` but only as a last resort (it will change your /etc/X11/xorg.conf, so you don't really want to resort to this if you've done any configuration in the past).

---

