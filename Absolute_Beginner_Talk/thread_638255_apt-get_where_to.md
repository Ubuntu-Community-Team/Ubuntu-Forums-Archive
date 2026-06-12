---
title: "apt-get where to?"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by mD3m4r415 on 2007-12-11
hello, when i install a program with apt-get like```
sudo apt-get update && sudo apt-get install gnome-do
``` where does said program end up?? because i want to install GNOME Do with it's plugins but i dont know where ```
~/.do/addins
``` is...
[http://do.davebsd.com/?q=content/download]("http://do.davebsd.com/?q=content/download")

---

### Post by gate on 2007-12-12
apt-get installs them into different places depending on the program. There are certain rules: Libraries e.g. 

```
apt-get intall libcurl4 
```

creates a file /usr/lib/libcurl.so.4

whereas 

```
apt-get install tremulous
```

 will install the game tremulous. There is usually a binary or script put in /usr/bin which is how just typing the word will execute the program, it looks in that directory. In the case of Tremulous, it is just a script that launches trem which is actually stored in /usr/lib/tremulous

if you want to know exactly what files and where they are put, y ou can go to 

[packages.ubuntu.com ]("http://packages.ubuntu.com")

for tremulous, the exact link is [packages.ubuntu.com/gutsy/games/tremulous]("http://packages.ubuntu.com/gutsy/games/tremulous")

installing sources almost universally (in my limited experience) places the source files in /usr/src


EDIT:
For non-standard repos, it is probably easiest to take the .deb from his repo, extract it and look at the contents manually.

---

### Post by rockinlinux on 2007-12-12
FYI the actual .deb package gets saved in /var/cache/apt/archives

---

