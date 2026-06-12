---
title: "Update mamager will no longer install."
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Linuxratty on 2007-11-05
This is my first day using Ubuntu and something like this happens.
 I have no idea how to fix this. 

EDPKG was interrupted You must manually ryn dpkg config ar to fix the problem. Huh
E _cache >open () failed.please report.

---

### Post by Maestro23 on 2007-11-05
> **Linuxratty said:**
> This is my first day using Ubuntu and something like this happens.
 I have no idea how to fix this. 

EDPKG was interrupted You must manually ryn dpkg config ar to fix the problem. Huh
E _cache >open () failed.please report.

Open a terminal: Apps>> Accessories>> Terminal

Then type the following commands:

> sudo dpkg --configure -a

sudo apt-get update

sudo apt-get upgrade


You will be prompted for your root password.  This is the same password that you use to login with. It will not echo (display) on the screen when you type it.  Just type it and hit ENTER.

---

### Post by Partyboi2 on 2007-11-05
try in a terminal
```
sudo dpkg --configure -a
```then:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```:):)

---

