---
title: "Lock file ?"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by dngn on 2007-01-10
I get this message any time I try to install from terminal can someone please help !!! 

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by viciouslime on 2007-01-10
Put sudo infront of the command you are using, so: sudo apt-get install *****

This will give you root privileges and so allow you to install

---

### Post by dngn on 2007-01-11
I don't know if I typed the command correctly.The program is crossover-pro and the extension ends with .sh .I have the folder extracted on the desktop but in both cases it says couldn't find package. 

Attempt # 1::sudo apt-get install crossover
                       Reading package lists... Done 
                       Building dependency tree       
                       Reading state information... Done
                       E: Couldn't find package crossover 

 Attempt # 2::sudo apt-get install /home/dngr/Desktop/install-crossover-pro-5.0.3.sh 
                       Reading package lists... Done
                       Building dependency tree       
                       Reading state information... Done
                       E: Couldn't find package

---

### Post by blackened on 2007-01-12
install-crossover-pro-5.0.3.sh is likely an install script. To run it cd to the Desktop directory then
```
sh install-crossover-pro-5.0.3.sh
```

Should automatically install itself from there.

---

