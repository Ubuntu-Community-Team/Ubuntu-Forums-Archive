---
title: "installing kate and c library"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by zakiya on 2008-04-19
Hi I have just installed Ubuntu for the first time. I want to install kate but " sudo apt-get install kate " gives "couldn't find package kate".
I've also tried "sudo apt-get install kubuntu" first as suggested in another thread but still "couldn't find package kubuntu".

Also how do I install the c library stuff, man pages etc? ( I am a computer science student learning c) 

Any help much appreciated,
Anna.

---

### Post by ibutho on 2008-04-19
KATE is part of the kdebase package. If you just want to install a base KDE and developments tools, run the Add/Remove Software application and search for kdebase and build-essential or run gnome-terminal and enter the commands below
```
aptitude update
aptitude install kdebase build-essential
```
If you want a complete KDE, then I suggest you install kubuntu-desktop instead of kdebase.

---

### Post by nrs on 2008-04-19
> **ibutho said:**
> 
If you want a complete KDE, then I suggest you install kubuntu-desktop instead of kdebase.

or just 'kde' if you want vanilla.

---

### Post by zakiya on 2008-04-19
```
aptitude update
```
could not open lock file /var/lib/apt/lists/lock_open (13 Permission denied)
couldn't open list directory ...are you root?

```
aptitude install kdebase build-essential
```
could not open lock file /var/lib/apt/lists/lock_open (13 Permission denied)
unable to lock the administration directory (/var/lib/dpkg/) are you root?

---

### Post by ibutho on 2008-04-19
My apologies, you need to prefix each command with sudo e.g.
```
sudo aptitude update
sudo aptitude install kdebase build-essential
```

---

### Post by zakiya on 2008-04-19
Okay thankyou, that seemed to install the packages but do I still need to install kate as i get "kate is not installed" if i try to open it from the terminal. Tried sudo apt-get install kate but "couldn't find package kate"

Can anyone give me a link to a guide to the different packages and how to install them, hate to bother people unneccessarily :)

---

