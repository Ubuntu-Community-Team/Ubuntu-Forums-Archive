---
title: "Gnome Desktop keeps rebooting"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Greglu on 2008-03-21
Hello all,
I just did a really daft thing.

I have had Gutsy working wonderfully for the past month or so.

Then today, I was messing around wiith the screen resolution on my laptop, as I had attached a second monitor to it.

Well one thing led to another and now whenever I log into Gutsy. Gnome loads then exits back out to the username/pwd screen.

Any help would be appreciated.

Cheers
Greg

---

### Post by dannystaple on 2008-03-21
Before anything else - look in the menu in the login screen - it should have a fail safe log in mode - try that first.. Failing this it gets more difficult.

One suggestion is to change the screen resolution setup from the command line - since you have locked yourself out of the GUI. If you press ctrl-alt-f1, then you will switch to a command line only terminal. Use your normal log-in details.

You will need to edit your xorg.conf file, which is in /etc/X11/xorg.conf, as a root user:
"sudo nano /etc/X11/xorg.conf".

The xorg.conf file contains the devices and their configuration for use in the Ubuntu GUI.

The file is documented here: [http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

You are interested in the Monitor, Screen and Modes sections.

---

### Post by Greglu on 2008-03-21
[FONT="Trebuchet MS"]Thanks for the tips,
I started in Gnome Safe mode and used the Restricted Drivers Manager to re-enable the Graphics driver.  For some reason it had been disabled.  Anyway, I think I Probably got lucky with this one.  I think I am going to see if t is possible to create an ISO image of my setup, that way if I have to rebuild my system then it should be relatively painless to quickly resurrect the system.

Cheers
Greg[/FONT]

---

