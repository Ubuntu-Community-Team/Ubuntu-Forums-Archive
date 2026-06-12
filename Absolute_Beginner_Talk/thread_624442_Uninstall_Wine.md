---
title: "Uninstall Wine"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by jmtjet on 2007-11-26
I installed Wine to run a couple of Windows games. But, wasn't successful in doing so. How do I uninstall Wine. Thanks.

Using Gutsy Gibbon.

---

### Post by jfinkels on 2007-11-27
If you installed wine using Synaptic or "apt-get" (or "aptitude"), just type in the terminal:```
sudo aptitude remove wine
```

If you used a .deb package to install it, then locate the package and type in the terminal:```
sudo dpkg -r *packagename*.deb
```

If you compiled and installed it yourself, in the directory in which you compiled wine (i.e. the directory that contains the Makefile) try :```
sudo make uninstall
```

Otherwise, you're going to have to find the files by hand and remove them manually.

Read the first link in my signature for more information on installing (and uninstalling) software in Ubuntu.

---

### Post by -grubby on 2007-11-27
```
sudo apt-get remove wine
```

---

### Post by jmtjet on 2007-11-27
I used: sudo apt-get autoremove wine,   which did the trick(I think)but Wine is still on my applications list. How do I get it off of the list. Thanks again.

---

### Post by jfinkels on 2007-11-27
Press <Alt>+<F2> and type:```
alacarte
```, locate the entry you wish to remove, and remove it!

---

### Post by jmtjet on 2007-11-27
Thanks, that did it. Boy you guys are sharp. :)

---

### Post by websnail on 2007-11-27
Not "autoremove" , instead you need use "remove" .
"remove" means uninstall the application(s) you specifies.
while "autoremove" means to purge old downloaded packages.

---

### Post by kpkeerthi on 2007-11-27
Wine keeps the files you installed in .wine folder under your HOME directory.

To check the disk space used up by wined application run
```

du -sh ~/.wine

```
and optionally delete the folder if you do not want to keep it

**Method 1:**
Recursively remove the contents of .wine
```

rm -rf ~/.wine

```

**Method 2:**
1. Open nautilus by clicking on the Home icon on your desktop
2. Press Ctrl + H to view hidden files
3. Scroll down and delete the .wine folder

---

### Post by jfinkels on 2007-11-27
Just had to comment on the irony of the command you told the OP to run, and your signature :D

---

### Post by websnail on 2007-11-27
And then wine progam group is in palce  ~/.local/share/applications/wine 
when uninstall wine or uninstall  programs from wine , you should delete the menu manually .

---

### Post by kpkeerthi on 2007-11-27
> **jfinkels said:**
> Just had to comment on the irony of the command you told the OP to run, and your signature :D

:) I realized that too. And that's why I suggested the OP **Method 2** :)

---

