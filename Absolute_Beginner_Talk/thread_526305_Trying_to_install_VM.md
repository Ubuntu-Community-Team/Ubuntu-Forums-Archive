---
title: "Trying to install VM"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Mac70 on 2007-08-15
Im a bit confused with this. Following the numerous tutorials Ive tried installing the necessary files (build-essential etc) but when it comes to the point of inserting my CD, Kubuntu Fiesty, nothing happens.
Is it trying to find something or write to the CD? I only have a cd-rom in this pc, though I can borrow the wifes writer.
Or is there some workaround?

---

### Post by zvacet on 2007-08-15
```
gksudo gedit /etc/apt/sources.list
```

Put # sign in front of the cdrom line and let it look like this

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

save the file and 

```
sudo aptitude update
```

After that try to install packages you need.

---

### Post by Mac70 on 2007-08-15
Thanks. Just away to have my dinner, but Ill let you know how it goes.

---

### Post by Mac70 on 2007-08-15
Worked perfectly, thanks again.:)

One more question. I used VMWare on XP last year, and didnt like the idea of starting every time I started up the pc, using up resources. Is it just "on-demand" on Linux? Then I can have a guess at how much memory to allow the vm to use.

---

