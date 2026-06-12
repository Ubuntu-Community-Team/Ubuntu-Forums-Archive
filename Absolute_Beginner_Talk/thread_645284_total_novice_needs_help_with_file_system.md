---
title: "total novice needs help with file system"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by robsarm on 2007-12-19
so I am trying to find where I used automatix to install swiftdove email so I can delete it manually as automatix will not remove it. On the command line I can use locate swiftdove and sure enough it finds  the directory and all the files in it. Unfortunately I am not familiar enough with the file system to know what this means: /home/rob/.swiftdove
what does the . before swiftdove mean. Thanks for the help and sorry for such a newb question.

---

### Post by spiderbatdad on 2007-12-19
the dot means it is a hidden file in your home directory. Open your home directory and choose the view tab, then show hidden files, and you'll see it.

---

### Post by macogw on 2007-12-19
. means it's hidden.  It's probably not only installed in your home drive though.  That'd be kind of odd.  the . files in your home drive generally just hold your settings.

Also, don't use Automatix.  It has been called "actively dangerous to systems" by Ubuntu developers, because it kind of stabs through things to do what it wants instead of saying "excuse me, could you let me through?"  Anything you need for codecs, multimedia, java, etc. can be gotten by getting "ubuntu-restricted extras" from Applications > Add / Remove

---

### Post by robsarm on 2007-12-19
thanks for the help. I have decided that automatix sucks. now I have to find and delete swiftdove then figure out how to uninstall automatix.

---

### Post by spiderbatdad on 2007-12-19
maybe```
sudo dpkg -r  --purge automatix
```

---

### Post by robsarm on 2007-12-19
cool thanks

---

