---
title: "how does the make command work exactly?"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by immranderson on 2007-10-16
hey, i'm trying to install compiz fusion right now, and I have the folder extracted from my tar.gz file onto my desktop titled compiz-0.5.2

now, upon inspection of the readme, it just says I need to make the file using auto make, then use the command make -- though i couldn't get auto make to work, so to be honest -- I have no clue what i'm doing as I've never really "made" a file or installed it on my own without copying and pasting what sites have told me to...

Thanks for any help in advanced!

---

### Post by BaffledMollusc on 2007-10-16
> **immranderson said:**
> hey, i'm trying to install compiz fusion right now, and I have the folder extracted from my tar.gz file onto my desktop titled compiz-0.5.2

now, upon inspection of the readme, it just says I need to make the file using auto make, then use the command make -- though i couldn't get auto make to work, so to be honest -- I have no clue what i'm doing as I've never really "made" a file or installed it on my own without copying and pasting what sites have told me to...

Thanks for any help in advanced!
The standard Linux mantra in these instances is
```

./configure
make
sudo make install

```
This will compile and install your source code. However, before you can do this, you need to install the compiler and build tools, since they're not installed by default. To do this you need to install the "build-essential" package. To install this package, go to System->Administration->Synaptic Package  Manager and search for the package by name.

If you still can't get it to work, post back here :)

Incidentally, are you sure you want to do this the hard way and build compiz from source? Can't you wait a couple of days and install Ubuntu 7.10 which has compiz enabled by default?

---

### Post by immranderson on 2007-10-16
well, to be technical -- i have ubuntu 7.10 right now, but I'd like to get the desktop cube effects and the like working :-)

---

### Post by jayaramk on 2007-10-16
it u need to know more indepth of there commands....... use man(help) in the terminal.... sat to know about make
type......

man make

man is used as an alias fior the help which is used in dos

---

### Post by RomeReactor on 2007-10-16
Hi. If you already have Gutsy, then all you need to install is **compizconfig-settings-manager** (look for it in Synaptic); or to install it from the terminal:
```
sudo apt-get install compizconfig-settings-manager
```

Once it's installed, go to "System->Preferences->Appearance", go to the "Visual Effects" tab, select "Custom" and press "Preferences". Disable the **Desktop Wall** plugin, and enable the **Desktop Cube** and **Rotate Cube** plugins.

---

