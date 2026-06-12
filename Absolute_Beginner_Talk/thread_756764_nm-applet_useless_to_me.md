---
title: "nm-applet useless to me"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by harrykh on 2008-04-16
Only because I use static IP addressing @office and @home. And if I choose "Manual Configuration" in nm-applet it forwards me to network-admin. 

it's kinda of weird though, after choosing manual nm-applet completely gives control to network-admin, so what use is it now that my interfaces is setup @ /etc/network/interfaces ? and that nm-applet won't ever touch those interfaces again ???

It basically a resource taking application running in my computer with already limited resources.

I tried uninstalling it from my system but I'd also have to uninstall ubuntu desktop :(

...nm-applet does provide me faster access to wireless DHCP. Is there like a complete program that does like what networking is in windows.

---

### Post by dave333 on 2008-04-16
If you want to turn off nm-applet you can do it this way:

Menu -> System -> Preferences -> Sessions

Un-tick Network Manager and reboot.

---

### Post by spiderbatdad on 2008-04-16
And why do you need ubuntu-desktop?
Don't confuse it with GDM.
Just unistall it.

---

### Post by john91 on 2008-04-16
Well, if you're not adverse to using the terminal, you could always take a look at this thread.  there's a great section near the bottom on static ip's.  

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

If you've already seen this thread, then I'm sorry for the redundancy.  As for saving your system resources, you can always just set nm-applet to not start at login.   In my experience, nm-applet won't start up on its own if you don't start it up at login.

---

### Post by harrykh on 2008-04-16
> **spiderbatdad said:**
> And why do you need ubuntu-desktop?
Don't confuse it with GDM.
Just unistall it.

o so ubuntu-desktop is not the desktop itself ? good to know I got several things I want to uninstall but ubuntu-desktop always comes up.

can i also safely uninstall firefox ? like when I tried it shows that i will also need to uninstall several other programs.

I didn't start nm-applet on my own, I didn't even install it. it came with the installation of 7.10 (downloaded like 3 days ago).

---

### Post by Lolicon on 2008-04-16
nm-applet doesn't really use many resources at all. Unless you have less than 1GB of ram I would just leave it alone. You can try wicd instead.

---

