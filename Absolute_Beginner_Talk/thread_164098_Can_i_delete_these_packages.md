---
title: "Can i delete these packages?"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by TheTux on 2006-04-22
hello

i found so many .deb packages in /var/cache/apt/archives ...are those packages still needed? can i just delete them...about 500 mb of them..i really need to free my hd...is there any directory that i can free?

---

### Post by Ecthelion on 2006-04-22
You can delete them.

In command line it's just 
```
apt-get clean
```
and then it get cleaned automatic

---

### Post by Ecthelion on 2006-04-22
I forgot to say, maybe you need to sudo that command

```
 sudo apt-get clean
```

---

### Post by Bloch on 2006-04-22
A .deb file is an installation file. Yes, you can delete these. If you need to reinstall a package it will be downloaded automatically (presuming you have an internet connection.
The other big space hogger is the documentation, and extra languages if you have them installed.
/usr/share/doc is about 100MB

Use apt-get remove --purge  to uninstall games etc
The default ubuntu installation is fairly minimal in comparision to other distributions - there is no TeX, compilers, extra files for programmers etc
It can be risky to delete stuff. You never know when it is needed. For example there is tons of Python stuff, but don't go near that as the system uses it.
Do a search for image files,(.gif, .jpeg) .html files and you should be able to delete all these. (as long as you don't delete your icons!)

But really, if you have to worry about 100MB, then it's time to get a new harddrive - do you know most computer boxes have space for a second harddrive? You can pick up a cheap 40GB disk and plug it in.

---

### Post by TheTux on 2006-04-22
okay ;p cleaned up....thanks

---

