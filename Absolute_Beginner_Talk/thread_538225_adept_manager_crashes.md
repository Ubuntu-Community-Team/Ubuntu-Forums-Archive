---
title: "adept manager crashes"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by MrBeenz on 2007-08-29
Ok Heres what happens When I go in the adept manager i click on Manage Repositories and a window pops up and says Installer Crashed and under that it says We're Sorry; software-properties crashed. Also I dont know if it matters but im using Kubuntu. Does anyone have any idea on how to fix this.

---

### Post by Happy_Man on 2007-08-29
Try the command ```
sudo apt-get remove --purge adept-manager
```, then type ```
sudo apt-get install adept-manager
```

---

### Post by MrBeenz on 2007-08-29
Thanks for trying to help but the same thing still happens

---

### Post by MrBeenz on 2007-08-30
How do completely remove it because when i reinstall it it uses the old package i have just deleted.

---

### Post by Happy_Man on 2007-08-30
Delete the package from /var/cache/apt/archives. That forces it to download a whole new copy.

---

### Post by Chelidon on 2007-11-27
I don't know if this is related but my Adept has a tendency to crash just by typing into the search bar. KDE in general has been more buggy for me than my old Ubuntu, my Synaptic worked fine. If I can get past the filtering process it works fine!

---

### Post by iblazev on 2007-12-14
Don't know if this is a problem with KDE but I have a similar problem with adept manager. Although it doesn't crash during work it does crash when I close the adept manager window (?!) with SIGSEGV 11 signal. It doesn't happen often. 

Since, I'm new with linux in general, if something like this continues does it effect the system in general or if I just remove adept and use synaptic or apt-get and deselect everything will be fine?

---

### Post by kuegel12 on 2007-12-14
I'm getting a crash about 15 % into the install procees, install not download, on just about anything i down load seems to have happened since my last update any ideas?

---

### Post by karim_eng on 2008-03-07
hey try this command
sudo dpkg --configure -a
it solved the problem when my adept manager crashed

---

