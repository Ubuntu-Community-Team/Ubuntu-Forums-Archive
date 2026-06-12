---
title: "[SOLVED] Ubuntu 7.04 overclocking nvidia video cards,"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by jake16424 on 2007-08-12
I had a topic started a while ago, but sense are unable to find it, i have recently installed my drivers to my suprize without help. now, i need to know the command to allow me to get into the utility to overclock and adjust the settings of my display. hardware goes as follows.

Nvidia Geforce FX5500 AGP 128mgs of ram.

---

### Post by benerivo on 2007-08-12
In synaptic (or adept if kubuntu), install the nvclock package.

---

### Post by jake16424 on 2007-08-12
i dont know what synaptic is, or adept, O_O... how would i go about doing that?

---

### Post by benerivo on 2007-08-12
The standard Ubuntu distribution (probably the one you are using) has a program called Synaptic which manages what programs (aka packages) you have installed, and has a list (aka repository) of what programs are available to install. It is accessible from the main menu. Start it and search for nvidia. You will get a list of all packages in the repository that have "nvidia" in the package name or desrciption. Choose the 'nvclock-gtk' package, and install it. When done, go to a terminal and type ```
nvclock_gtk
```

---

### Post by jake16424 on 2007-08-12
cool thank you, i will install the package =) how if i may inquire do i make a launcher to launch this command

sudo nvidia-settings


instead of using the terminal to launch it? so i only have to click a button?

---

### Post by benerivo on 2007-08-12
Well, I use kde rather than Gnome, which i'd guess you are using, but it may be along the same lines...

If you right click on the desktop and try to create a new shortcut to an application, you may be given a new window that asks for some info on what you want to try and run. Just use the command nvidia-settings (i don't think you'll need sudo but others may help you more on this one). This should make a desktop shortcut for what you want. 'Shortcuts' like this may be made as startup programs or as new items in the main menu, or desktop panel.

---

### Post by tadada on 2007-08-12
you probobaly will need to replace sudo with gksudo (the difference is that sudo is terminal and gksudo is graphical both ask for admin password)

---

### Post by jake16424 on 2007-08-12
well guy's i got everything working, and i have my launchers set up, it was easy thanks to you guys, =) i owe you some :popcorn:

:) well, thankyou

---

