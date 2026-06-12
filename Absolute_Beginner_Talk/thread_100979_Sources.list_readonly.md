---
title: "Sources.list readonly?"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by SomethingTohide on 2005-12-08
I browsed to this file to change something, but it's readonly and I can't change that, what do I have to do?

---

### Post by aysiu on 2005-12-08
If you're in Gnome, Alt-F2 ```
gksudo nautilus
```
If you're in KDE, Alt-F2 ```
kdesu konqueror
```

If you prefer the Terminal or Konsole, ```
sudo nano /etc/apt/sources.list
```

---

### Post by towsonu2003 on 2005-12-08
write permission is given only to root. to edit: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo gedit sources.list 
```
sudo gives root privileges, so be careful :)
once your edit is done, save and close gedit window. 

PS assuming u use ubuntu, gedit is your text editor. you can also use nano (no need for X with nano).

---

### Post by SomethingTohide on 2005-12-08
Ok thanks that works. And I'm trying to install Opera using the apt-get method and it's giving me this...

The following packages have unmet dependencies:
  opera: Depends: libqt3c102-mt but it is not installable
E: Broken packages

---

### Post by Qrk on 2005-12-08
Opera depends on qt (KDE). Install KDE base; including the libs you mentioned, and you'll be all set.

Personally, the easiest thing to do is to install k3b first. It depends on everything that Opera needs to run and is a great app that doesn't have the best Gnome substitute. Its also availabe from the repositories.

---

### Post by SomethingTohide on 2005-12-08
I just got the k3b and KDE with all things included installed from repos. but it still gives me that error

---

### Post by Qrk on 2005-12-08
hmm. Try fixing the package. Open synaptic and go to Edit-->Fix broken packages. That should make it work.

---

### Post by SomethingTohide on 2005-12-08
It wasn't broken, but I just installed a lottt of packages and it worked.

---

