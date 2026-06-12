---
title: "About Root In Live CD"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by geragmx37 on 2005-11-30
I really want to know Why I entered in UBUNTU with a Live CD with ROOT privileges (I used a root terminal) but when I installed the system in my PC with a double booter (GRUB) I tried to use the same terminal but appears a message in the bottom of the screen that says that is loading the program but suddenly the system stops what it was doing and the clock-cursor reverts to an arrow again. When I tried to use another program the system Informs me that I need a Root password (something I never needed when I used the Live CD). Is this some kind of a catch? Can anybody tell me how I can use my UBUNTU system with the ROOT privileges?

Any help will be hot?

---

### Post by aysiu on 2005-11-30
The live CD is designed not to harm your hard drive--even with root privileges. It's run completely off the CD itself and your computer's RAM.

The installation CD is on your hard drive and is protecting you from yourself and from the internet.

If you find yourself configuring a lot of things right after installation, and you prefer to do things graphically (point and click), I'd advise creating a launcher (right-click on the panel > Add to Panel > Custom Application Launcher) with the command ```
gksudo nautilus
``` This launcher, when clicked, will give you a new file browser window with temporary root privileges.

If you prefer the terminal, just preface every new command that needs root privileges with the word *sudo*. For example, instead of ```
gedit /boot/grub/menu.lst
``` you'd write ```
sudo gedit /boot/grub/menu.lst
```

For more on this, see [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

