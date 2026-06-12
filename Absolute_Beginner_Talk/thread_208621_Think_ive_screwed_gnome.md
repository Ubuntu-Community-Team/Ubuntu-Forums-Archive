---
title: "Think ive screwed gnome"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by Brokenrgv on 2006-07-03
was trying to install through synaptic a dependency for gnokii for my phone pressed install and watched as this little bugger started to uninstall all the gnome stuff, ive done this in the past and when ive gone to restart ive ended up with just command line, when i go to synaptiv and check gnome its not installed now, it is supposed to be isnt it, do i need to start going through all the dependency's for gnome again and install it? sorry im kind of a linux newb.

---

### Post by T700 on 2006-07-03
You could go to a terminal and type:

[SIZE=2]aptitude install gnome-desktop-environment

[/SIZE]to replace anything critical that's missing.

Paul

---

### Post by Brokenrgv on 2006-07-03
thanks m8 im trying to go through all the dependency's again to re install it, the thing even uninstalled terminal on me fortunately i have Konsole, while it was uninstalling everything i panicked and forced quit before more "damage" was done was this the right thing to do?

it wasnt gnokii it was gnome phone manager, just to clarify, one other question when aptitude is working out dependency's and comes back with a solution is it generally ok to accept the first solution?

---

### Post by catlett on 2006-07-03
Synaptic Package Manager will show what it is going to uninstall and you can say no. If you still execute the installation then it will uninstall everything it said.
If you are using the terminal. Use aptitude instead of apt-get. It will also let you know what will be removed. Plus it will try and resolve your dependency issue. Sometimes what apt-get or synaptic says needs to remove all of gnome to get. Aptitude only holds a package at it's current version and the problem is solved.

If you are still having trouble recovering from the uninstall just do an update/upgrade
```
sudo aptitude update 
``````
sudo aptitude upgrade
``` Then try installing the package with aptitude ```
sudo aptitude install gnokii
``` Aptitude will install the dependencies for you. And if you have to remove a bunch of stuff to resolve it, it will give you the chance to abort

---

### Post by Brokenrgv on 2006-07-03
sorry for all the newb questions but when is it safe to assume that you have gnome back to a bootable setup, when its showing up as installed in synaptic?, im kinda scared to reboot since last time i was left with nothing but command line, which i still suck at very much.
Its anoying how one little program can screw up so much of your system, allmost virus like. This will teach me to check in synaptic what its going to change before pressing ok.

update: Ive reinstalled gnome-desktop-manager and gnome through synaptic and rebooted fine, panicked for nothing thanks for the reply's :)

---

### Post by catlett on 2006-07-03
Don't apologise. You were right to not reboot and post. You can reinstall and fix your system if you don't reboot.
If you rae ever not sure if you have everything installed that you have to, just run an aptitude dist-upgrade. Aptitude will make sure everything is installed for your version of Ubuntu, and all dependencies taken care of.
```
sudo aptitude update
```
```
sudo aptitude dist-upgrade
```

---

