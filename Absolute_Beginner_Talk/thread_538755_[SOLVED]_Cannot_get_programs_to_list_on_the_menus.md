---
title: "[SOLVED] Cannot get programs to list on the menus"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by javicadena on 2007-08-30
All, I am new to linux (4 days), experienced w/ computers.  Installed 7.04, love the speed, etc.  However, I am trying to get the programs that I have installed to display in the menus.  I go through the control panel and into main menu and then check the ones that I want to display, however, I cannot get debian to display, it is there, I click on it, then close the window, and is not in my applications menu.  This happens to debian, alien, gzip.   
It seems that the programs are installed, but do not get put into the different categories.  Any suggestions

---

### Post by forestpixie on 2007-08-30
To get debian menus to work I do these 3 - in terminal

```
sudo apt-get install menu
sudo apt-get install menu-xdg
sudo update-menus
```

which I found in a thread

---

### Post by mcduck on 2007-08-30
for the debian menu you need to install some package, I can't just now remember which one.

Alien and gzip are command-line programs, menu entries for them would be rather useless.

---

### Post by Lord Illidan on 2007-08-30
Alien is a command line application, so it won't be much use from the menu..
Debian? Do you mean the Debian menu? Not much use.

---

### Post by wolfen69 on 2007-08-30
to add to the menus: system>preferences>main menu

---

### Post by javicadena on 2007-08-30
Thanks everybody, got it solved!!!  I guess needed to run the instructions in the terminal

---

