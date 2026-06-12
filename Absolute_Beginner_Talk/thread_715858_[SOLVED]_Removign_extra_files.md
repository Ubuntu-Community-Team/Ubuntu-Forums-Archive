---
title: "[SOLVED] Removign extra files"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by computermesh on 2008-03-05
I've been downloading some games and trying them out off and on. Then uninstalling them if i dont like them. Is there a way or a command to remove all the extra things like the libraries that came with them? I noticed that alot more things were downloading. For example i selected to download one game and it had to download 12 other things with it.

---

### Post by glennric on 2008-03-05
You can use
```
sudo apt-get autoremove --purge packagename
```
where packagename is the name of the game (or application) you originally installed.  This will remove all of the dependencies that were installed when you installed the game (or application) originally.

---

### Post by computermesh on 2008-03-05
ok now the problem is that ive been doing this over a day or 2....what if i dont remember all the games? another way to check for unused files/libraries?

---

### Post by jan quark on 2008-03-05
try only

```
sudo apt-get autoremove
```

---

### Post by computermesh on 2008-03-05
this is what i get as an output

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by computermesh on 2008-03-05
does that mean it couldn't find any? or was that not the correct command? any ideas?lol

---

### Post by w0ng on 2008-03-05
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

Do the steps for:
Remove Residual Config packages
Remove partial packages
Install localepurge in Ubuntu
Install GtkOrphan in Ubuntu

---

