---
title: "Ubuntu 7.10 Requiring CD for some programs"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-11-23
Is there a way I can stop this and put whatever is on the CD on the computer itself?

Disc space is no object.

---

### Post by taurus on 2007-11-23
You can edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line to comment out the cdrom so it will not ask you for it from now on.

Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mahiyar on 2007-11-23
Or you can do this >System>Administration>Synaptic package manager> settings>Repositories and from the Ubuntu software tab uncheck the "Installable from CD ROM"

---

