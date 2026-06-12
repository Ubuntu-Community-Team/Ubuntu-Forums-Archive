---
title: "Problem with dpkg --configure -a"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by BlueTree on 2007-05-24
I get this error when I try to do anything with a package manager (synaptic or the updater). I try to enter the command 'dpkg --configure -a', and a EULA for Skype comes up. This problem only started after I tried to use EasyUbuntu to get Skype. I now can use Skype, but I cannot access EasyUbuntu- it says something about starting it, and then nothing happens. It claims that it is open in the system manager, but I can do anything with it. I just want to get things working normally again... help?

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by taurus on 2007-05-24
Open a terminal and type

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by BlueTree on 2007-05-24
[COLOR="Red"]As I said, I already tried that. The problem is:

when I enter 'sudo dpkg --configure -a', it brings up a EULA (End User License Agreement)for Skype. I cannot enter the following three lines of code, because there is nowhere to do so. The EULA is in the Terminal, and blocks me from doing anything else there.[/COLOR]

I figured out how to get past the EULA. Thank you very much for your help.

---

