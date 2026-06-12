---
title: "Can't install any software and can't update too!!help!!"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by jaywee on 2007-05-02
several days ago I was too boring to do anything else, so I delete all the files under /var/cache/apt/archives, because it is said all these files are installed software packages, I thought they are useless. Then here comes a big problem, when I type apt-get install * or apt-get update, the terminal will give the hint that could not open lock file  /var/cache/apt/archives/lock - open, and unable to lock the download directory, I'm mad about this, hope someone could help me !!!!

I do 
```
sudo mkdir /var/cache/apt/archives
sudo mkdir /var/cache/apt/archives/lock
sudo aptitude update
sudo aptitude upgrade
```
as taurus said. now I can do 
```
sudo apt-get update 
```
and 
```
sudo apt-get dist-upgrade
```
but, there is still a problem that I can't install ,when I do 
```
sudo apt-get install *
```
I got the message:
```
E:could not open lock file  /var/cache/apt/archives/lock - open(21 is a directory)
E:unable to lock the download directory!
```
so who can help to fix that??
thanks!!:confused: :confused:

---

### Post by starcraft.man on 2007-05-02
Ummmm, uhhh... *blinks blankly at what he just read on screen* Oooookayyy. Ummm, I don't know if we can fix that... I'm pretty sure since thats the programs you installed its unique to your install... anyone know?

Might have to reinstall... not sure, suggestion though for future... don't delete files not in home folder >.>

---

### Post by zvacet on 2007-05-02
[http://ubuntuforums.org/showthread.php?t=429522&highlight=var%2Fcache%2Fapt]("http://ubuntuforums.org/showthread.php?t=429522&highlight=var%2Fcache%2Fapt")

---

### Post by jaywee on 2007-05-03
Thanks a lot!! but still some problem!

---

### Post by jaywee on 2007-05-03
hope someone could help me !!please!!

---

