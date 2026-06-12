---
title: "Download Deps but Not Install"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Ryan H on 2007-03-30
I was wondering if there is an automates tool to download the dependancies of a file, and their respective dependancies, but not install them, or if there is an option on Synaptic Package Manager. The reason being my friend wants Ubuntu but in order to setup his wireless card I need to install some things, and I don't want to hunt them all down manually.

Any help would be greatly appreciated!

-Ryan H

---

### Post by yabbadabbadont on 2007-03-30
```
sudo apt-get -d install packagename
```
Should do the trick.

---

### Post by Maestro23 on 2007-03-30
Also in the GUI(Synaptic), there's an option to "Download package files only". Will d/l, but not install them.  Just check the box  after you mark for installation and get reeady to download.

---

### Post by jerryrw on 2007-03-30
Then the files will be located in  /var/cache/apt/archives

---

### Post by Ryan H on 2007-03-31
Thank you! That's exactly what I needed! But is there a way to do it with the 32-bit repositories, I'm currently running 64-bit but he will be installing the 32-bit version.

-Ryan H

---

### Post by Ryan H on 2007-03-31
Could I just add the 32-bit repositories?

-Ryan H

---

