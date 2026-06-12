---
title: "Removing things from the application bar that arent in add/remove"
date: 2005-07-31
forum: Absolute Beginner Talk
---

### Post by lifewillfadeaway on 2005-07-31
How to do so?

---

### Post by Sam on 2005-07-31
Use Synaptic (System, Administration). Every package installed are there. Read [this](http://ubuntuguide.org/#synaptic).

You must know the package name, though. Tell what you want to uninstall if you cannot find by yourself.

---

### Post by lifewillfadeaway on 2005-08-01
Say it was Enemy Territory and its just the icon so its not listed in synaptic?

---

### Post by Sam on 2005-08-01
If the program isn't in Synaptic, you need to manually remove the folder containing the program the delete the launcher(s). Otherwise Synaptic do the job itself !

---

### Post by lifewillfadeaway on 2005-08-01
I removed the file itself, just dont know where theshort cut for the applications bar is :)

---

### Post by Sam on 2005-08-01
To list any file on your filesystem maching a pattern:
```
$ locate <pattern>
```

e.g:
```
$ locate Enemy
```

---

### Post by lifewillfadeaway on 2005-08-01
Finds nuthin =D
but its still in the Applications menu under Other

---

### Post by Sam on 2005-08-01
Go in directory /usr/share/applications, you'll find your file there.

---

### Post by lifewillfadeaway on 2005-08-01
=( Not in there either. Man these things hide well

---

### Post by lifewillfadeaway on 2005-08-01
NM got it!!
it was in /usr/share/gnome/apps/Games
 :)

---

