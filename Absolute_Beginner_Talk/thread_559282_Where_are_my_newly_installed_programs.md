---
title: "Where are my newly installed programs?"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by jupetsu on 2007-09-25
I have managed to install ZSNES yesterday using synaptics manager. I am just wondering where am I supposed to find the "executable"? It didn't appear on the applications/games menu. And how am I supposed to put it there?:confused:

---

### Post by mesilliac on 2007-09-25
Try opening a terminal (Applications > Accessories > Terminal) and typing "zsnes". If this works, you can add an entry to your menu by going to System > Preferences > Main Menu, selecting where to put the new entry and clicking "Add item". For the command, just put "zsnes".

To see a list of the files a particular package installed using synaptic package manager, just select the package and click "properties", then go to the "installed files" tab.

Executables are usually put in /usr/bin, but browsing this directory can take a long time. In the installed files view you should be able to find something like "/usr/bin/zsnes" which will be the location of your executable.

---

### Post by njknight on 2007-09-25
You can also type whereis ### or which ### or locate ### (### = the program name) into a terminal window

---

### Post by 3rdalbum on 2007-09-25
Look in my signature for a guide and a screencast.

---

### Post by mcduck on 2007-09-25
Basically all user-level programs put their executables into /usr/bin.

If you don't find it there use the 'which'-command, it will tell you path to a program's executable. For example running 'which firefox' will respond '/usr/bin/firefox'.

---

