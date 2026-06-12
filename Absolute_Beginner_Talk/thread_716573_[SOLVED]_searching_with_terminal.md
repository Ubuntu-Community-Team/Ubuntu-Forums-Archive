---
title: "[SOLVED] searching with terminal"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by weezy8802 on 2008-03-06
there is a way to search using the terminal it is similar to the apt-get command. i would appreciate any help.

---

### Post by hyper_ch on 2008-03-06
what do you want to search? Files/Folder? Software in the repositories? Content within files?

---

### Post by jr.gotti on 2008-03-06
first run "sudo updatedb"

then when that finishes "locate *file*" will search your index for all filenames containing / named *"file"*

---

### Post by Arthur Archnix on 2008-03-06
Do you mean search your computer, or search for programs and packages using apt?

If the former, do
```
sudo updatedb
```
then you'll be able to search using the locate command, e.g.
```
locate xorg.conf
```

If the latter then it's apt-cache search, e.g.
```
apt-cache search terminal --names-only
```

For more information, try:
> man updatedb
man locate
man apt-cache

---

### Post by weezy8802 on 2008-03-06
I want to be able to locate files to install from my terminal.

---

### Post by hyper_ch on 2008-03-06
then use "locate" and "updatedb" or use "find"

---

### Post by Kevbert on 2008-03-06
You can use 

apt-cache search filename 

where filename is the package that you want to find.  All files relating to the package will be listed.
Alternatively you could try

apt-cache search filename | grep file

where all packages contain the name 'file'.
I believe the search gives the same results as Synaptec Package Manager.

---

