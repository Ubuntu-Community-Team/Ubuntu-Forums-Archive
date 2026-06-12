---
title: "Ubuntu 6.10 install problem cannot log in.."
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-03-24
:( Alas Ubuntu has installed...however...It seems to boot fine, I enter user name and password, the desktop starts to load then the screen flashes a couple of times , then returns to the main login screen. What to do?

---

### Post by bulldog on 2007-03-24
Try hitting CTRL-ALT-F1 to get to a console.
Login and see if you can,so it eliminates you're giving wrong login information.

If you can login in console,there should be something wrong with the xserver.
After login [text mode] type in your console ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
so the xserver will be reconfigured.
Try a reboot and hope fully you can login as it should be in a graphical environment.

---

### Post by mramsey on 2007-03-24
No Dice... still having the same problem.  Could this PC just be not enough to run ubuntu properly? PII 400Mhz 256MB RAM

---

### Post by mramsey on 2007-03-24
I don't get it... it takes the user and password, the little nautilus box appears, sometimes the desktop starts to load and populate then all of the sudden I get kicked back out to the login screen.

---

### Post by bulldog on 2007-03-24
Did the live cd run without trouble or did you use the alternate cd.

I don't get it either,but if it starts to load your login should be right.

Well your PC isn't the latest model and I have no idea of your graphics,but it should run,although it will be a little slow.

---

### Post by mramsey on 2007-03-24
I had to use the 'noapic apci=off' in the boot command. then it finally worked for me. I don't know what to do at this point.

---

### Post by bulldog on 2007-03-24
Maybe you should try Fluxbuntu,it is less resources consuming and maybe it runs better on your system.
Otherwise I shouldn't know what's wrong with the thing.

---

### Post by mramsey on 2007-03-24
last ditch effort....I am trying 512MB RAM to see if that has any effect.

edit: I did get an error finally the panel poped  up and said something to the effect : 

error starting GNOME settings Daemon.....

Unable to determine the address of message bus (Try  'man dbus-daemon' and 'man dbus-launch' for help)

---

