---
title: "[SOLVED] Access to folder owned by root (me)"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by ozzyprv on 2007-12-12
Background:
~ I recently made a fresh install of 7.10
~Before the re-install, I had 7.04
~Before the re-install I moved all the files and folders I had @ /home to my 2nd HD (fat32)
~I had a samba sub-folder inside the \home\user folder
~That folder "samba" was/is owned by root

Problem(s)
~I cannot "see" the files within the samba folder that is now @ my 2nd HD. When open, it shows like empty.
~I cannot move the samba folder to my newly created \home. I am not the owner.

Any help?

---

### Post by mikewhatever on 2007-12-12
Try, alt+f2, gksudo nautilus, then navigate to the directory you want.

---

### Post by ozzyprv on 2007-12-13
> **mikewhatever said:**
> Try, alt+f2, gksudo nautilus, then navigate to the directory you want.

Is this for Ubuntu?
It does not work. A windows pops up and ask my about running something....

---

### Post by markusf21 on 2007-12-13
> **mikewhatever said:**
> Try, alt+f2, gksudo nautilus, then navigate to the directory you want.Yes this Is right ALT + F2 brings up a launcher then you type in gksu nautilus.
This runs nautilus as root so you an move whatever you want.

---

### Post by mikewhatever on 2007-12-13
> **ozzyprv said:**
> Is this for Ubuntu?
It does not work. A windows pops up and ask my about running something....

Just follow it step by step and see what happens.

---

### Post by jaybombalous on 2007-12-13
> **ozzyprv said:**
> Is this for Ubuntu?
It does not work. A windows pops up and ask my about running something....

no offense, but u gotta be a little smarter then the PC. Once the program pops up u need to type in.


```
gksudo nautilus

```

and hit enter. The explanation is that gksudo is the graphical version of sudo which will give u temp access to root. The nautilus is the file manger program, so when u type that into the 'run' program it will open up nautilus with root privileges so u can have access to files and folders that are owned by root.

---

### Post by ozzyprv on 2007-12-13
> **jaybombalous said:**
> no offense, but u gotta be a little smarter then the PC. Once the program pops up u need to type in.



Don't worry, I am proud of my n00b status.
The only way to learn is by reading, trying and asking. 

Thanks!

---

### Post by SunnyRabbiera on 2007-12-13
sudo is not root by the way, when you use ubuntu you use sudo that can give you root access but only if you type in sudo and your password in a terminal or if you use root apps like synaptic

---

