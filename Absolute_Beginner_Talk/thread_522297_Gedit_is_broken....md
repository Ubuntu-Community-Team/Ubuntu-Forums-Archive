---
title: "Gedit is broken..."
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Wobblebottom on 2007-08-10
Whenever I try to do anything with gedit, I get the following error


Segmentation fault


what does this mean?

---

### Post by SOULRiDER on 2007-08-10
Try reinstalling it and see if the problem persists:
```
sudo aptitude install gedit
```

Good luck!

---

### Post by Rocket2DMn on 2007-08-10
> **SOULRiDER said:**
> Try reinstalling it and see if the problem persists:
```
sudo aptitude install gedit
```

Good luck!

you're going to have to remove it first, otherwise it will tell you the latest version is already installed
```
sudo apt-get remove gedit
sudo apt-get install gedit
```
Long story short, a segmentation fault is when the program tries to access something outside of the memory that the OS gives it.  This throws up red flags and the program gets booted from memory.  It's nothing you did.

---

### Post by Wobblebottom on 2007-08-10
So this is what happened when I tried to uninstall gedit

Obontoe@Ubantoo:~$ sudo apt-get remove gedit
Password:
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
Obontoe@Ubantoo:~$


I'm confused.

---

### Post by Rocket2DMn on 2007-08-10
Try running
```
sudo apt-get update
sudo apt-get upgrade
```
If the problem with gedit happens after this, then try the uninstall/reinstall again.

---

### Post by stchman on 2007-08-10
> **Wobblebottom said:**
> So this is what happened when I tried to uninstall gedit

Obontoe@Ubantoo:~$ sudo apt-get remove gedit
Password:
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
Obontoe@Ubantoo:~$


I'm confused.

Try:

sudo apt-get autoremove gedit

---

### Post by Wobblebottom on 2007-08-11
> **stchman said:**
> Try:

sudo apt-get autoremove gedit



This action is met with this response;


E: Invalid operation autoremove


    ;__;

---

