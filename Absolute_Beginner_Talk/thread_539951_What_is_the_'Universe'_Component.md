---
title: "What is the 'Universe' Component?"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Hazmat. on 2007-08-31
Well, when i try to install beryl, when i type beryl-manager to get it running for the first time, it says something about the 'universe' component, and how can i enable it/check if i have it enabled? :)

---

### Post by oldos2er on 2007-08-31
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Hazmat. on 2007-08-31
Software properties doesn't appear.
I'm running on fiesty.
Theres only "software sources".
Nevermind, got beryl installed, i already had it enabled.

---

### Post by expatCM on 2007-08-31
so use the command line ....

sudo pico /etc/apt/sources.list 

read what is there and remove the line comments to enable a repository ....

then also from the command line ...

sudo apt-get update

---

### Post by wormser on 2007-08-31
> **Hazmat. said:**
> Software properties doesn't appear.
I'm running on fiesty.
Theres only "software sources".
Nevermind, got beryl installed, i already had it enabled.

Software Sources is what you want to enable universe.

---

