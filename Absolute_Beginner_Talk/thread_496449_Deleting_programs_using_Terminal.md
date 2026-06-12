---
title: "Deleting programs using Terminal?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by ellster456 on 2007-07-09
Ok I've figured out that the Terminal is the Linux version of Command Prompt... and I've successfully used it to install one application... my problem is there are two programs that I have installed and were not to my liking. I did not install them using Terminal, they auto-installed I guess. I have tried removing them using Add/Remove but it says they are being used for something. Is there an option such as ALT + TAB + DEL that I can see if they are still running ( which I doubt but can't say for sure) and if they're not, how do I use Terminal to delete them?

---

### Post by felicity on 2007-07-09
What programs are they?

---

### Post by Rui Pais on 2007-07-09
> **ellster456 said:**
> Ok I've figured out that the Terminal is the Linux version of Command Prompt... and I've successfully used it to install one application... my problem is there are two programs that I have installed and were not to my liking. I did not install them using Terminal, they auto-installed I guess. I have tried removing them using Add/Remove but it says they are being used for something. Is there an option such as ALT + TAB + DEL that I can see if they are still running ( which I doubt but can't say for sure) and if they're not, how do I use Terminal to delete them?

You got top on terminal and got gnome-system-monitor (on menus or from command line) to see running process and kill them.

To delete apps installed by debs (using apt, aptitude, synaptic or Add/remove) on command line you can do:
sudo apt-get  remove <app_name>

Command line has a very useful feature called auto-completion.
just type 3 or 4 letters of the word you want to type and press [TAB] and it will complete correctly for your (or give a list of option). Same goes for application names. Just type sudo apt-get remove and 3 or 4 first letters of application name and press tab will complete the correct name for uninstall or list possible ones.

---

### Post by hyper_ch on 2007-07-09
to find out more on apt-get or aptitude enter this in the terminal:

```

man apt-get

```

```

man aptitude

```

---

