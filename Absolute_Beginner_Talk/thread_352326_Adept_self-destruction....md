---
title: "Adept self-destruction..."
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Scale on 2007-02-03
I am quite new to Ubuntu and the Linux world in general, so I expected to make some bad mistakes and was prepared for the consequences, but sure I didn't expect Adept to destroy the system upon a simple uninstall request. I am using kUbuntu Edgy 6.10. I was trying to remove Python 2.4 to replace it with 2.5. 

I assume trying to remove the "minimal set of commands" package was the mistake? Appearently it triggered a mass unistalling of other packaged that completely crushed the system in less than the five seconds it took me to realize what was happening and close Adept.

In five seconds Adept uninstalled itself, Konqueror, the desktop manager GUI, the system manager GUI, other default programs like Kate and Gwenview, and several unrelated applications like Eclipse. Appearently it killed a lot of drivers and settings too, since internet (rp-pppoe) no longer works and upon reboot the screen settings were gone.

At least I think this is what happened, I cannot be sure (thought I have clearly seen adept remove itself and some drivers before closing). I cannot verify what happened because most menus have disappeared and I dont know the environment enough to navigate with the console. What I am sure of is that I had only selected 3-4 Python related packages for uninstalling.

I know it's my mistake, from now on I will always preview all changes before committing them (and make system backups, I have installed since about a month and haven't tried out everything yet). But is reformatting/reinstalling the only option at this point? Is there a way to recover the essential packages from the LiveCD?

---

### Post by slimdog360 on 2007-02-03
did you try ```
sudo apt-get install kubuntu-desktop
```? Id imagine that would reinstall the things you destroyed.

---

### Post by 3rdalbum on 2007-02-03
From the Live CD: Probably not.

From the Internet or an Alternate CD: Type ```
sudo apt-get install kubuntu-desktop
``` into a terminal on your borked system.

It's recommended that you keep all packages that were installed along with the base system. You can install Python 2.5 alongside 2.4.

---

### Post by Scale on 2007-02-05
Worked fine, thank you! Quite impressive it could recover seamlessy from such a situation.
I still have a problem though: there are no panels any more on the the taskbar save for the lower left links to applications; the main menu, virtual desktop selector, clock and notification icons are missing.
Other than that everything seems to be in place.

---

