---
title: "Why can't I access /proc/ ?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by John E on 2007-02-05
If I login as myself, I can double click on my 'Computer' icon, then 'FileSystem', then 'proc' and I can see all the files inside /proc/. However, if I try to do the same thing when logged in as **root**, it never works (I just get an indefinite timer cursor). Has anyone else seen this problem? :confused:

---

### Post by aktiwers on 2007-02-05
Works fine for me..  sorry dont know what your problem is. Just wanted you know that I have no problem doing this as Root.
EDIT: Actually I can go there as User too..

---

### Post by jordanmthomas on 2007-02-05
what happens if you try to navigate to /proc in a terminal?
does something similar happen?
```
cd /proc && ls
```

---

### Post by John E on 2007-02-05
Accessing /proc/ from a terminal window seems to work fine.

---

### Post by jordanmthomas on 2007-02-05
then the permission error makes no sense to me.  :(

---

### Post by John E on 2007-02-07
I wonder if this might have been a bug of some sort? Having done a complete update this evening, the problem's gone away. Or at least, it's changed - I can now access /proc/ but all the folders  have a read-only icon (lock) when I'm logged in as 'root' - but not when I log in normally.

Still confused.... :confused:

---

