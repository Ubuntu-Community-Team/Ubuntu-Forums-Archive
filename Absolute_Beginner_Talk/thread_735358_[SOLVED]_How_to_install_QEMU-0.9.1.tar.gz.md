---
title: "[SOLVED] How to install QEMU-0.9.1.tar.gz"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-03-25
Im not so good with these .tar.gz stuff so, pls help

---

### Post by aysiu on 2008-03-25
You don't want to use the package manager to install it? ```
sudo apt-get install qemu
```

---

### Post by munch3 on 2008-03-25
I try to install a .deb package and it says ''there is another internet operation running like snaptic etc.pls shoutdown'
when I run synaptic it says
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


when I run dpkg --conf...from therminal it says 'reuires superuser privilege'

---

### Post by munch3 on 2008-03-25
umm...
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


---

### Post by kellemes on 2008-03-25
type:
```
sudo dpkg --configure -a
```

---

### Post by aysiu on 2008-03-25
> **munch3 said:**
> umm...
```
sudo dpkg --configure -a
```

---

### Post by forrestcupp on 2008-03-25
> **munch3 said:**
> I try to install a .deb package and it says ''there is another internet operation running like snaptic etc.pls shoutdown'
when I run synaptic it says

when I run dpkg --conf...from therminal it says 'reuires superuser privilege'

Superuser privileges means you have to put **sudo** before the command.

Also, make sure you're not trying to run Synaptic *and* automatic updates at the same time.  And make sure Synaptic isn't open if you are typing apt-get something.  You can't do 2 Apt things at once.

---

### Post by munch3 on 2008-03-25
I try to install a .deb package and it says ''there is another internet operation running like snaptic etc.pls shoutdown'
when I run synaptic it says
Quote:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
when I run dpkg --conf...from therminal it says 'reuires superuser privilege'

---

### Post by arochester on 2008-03-25
command is:> sudo dpkg --configure -a

---

### Post by munch3 on 2008-03-25
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 .

---

### Post by Diabolis on 2008-03-25
You already have some answers, type **sudo** before the command.

> Superuser privileges means you have to put sudo before the command.

Also, make sure you're not trying to run Synaptic and automatic updates at the same time. And make sure Synaptic isn't open if you are typing apt-get something. You can't do 2 Apt things at once.

[http://ubuntuforums.org/showthread.php?p=4585457#post4585457](http://ubuntuforums.org/showthread.php?p=4585457#post4585457)

---

### Post by munch3 on 2008-03-25
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 .

---

### Post by munch3 on 2008-03-25
> **Diabolis said:**
> You already have some answers, type **sudo** before the command.



[http://ubuntuforums.org/showthread.php?p=4585457#post4585457](http://ubuntuforums.org/showthread.php?p=4585457#post4585457)

I like ur avatar ^^

---

### Post by FrozenFox on 2008-03-25
In regard to "E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? ":

You cannot use synaptic, the update manager, the add/remove programs tool, adept, or any command line dpkg/apt-get/aptitude tool simultaneously because they all use the same backend (dpkg) and trying to use it from multiple fronts will not work (designed that way I imagine for system stability reasons). Every time you try, you will get that error. If you are absolutely sure you are not trying to run more than one of the aforementioned multiple methods of software installation at once on accident, just reboot and it will be fixed (only do so if you dont have any updates working in the background!!). Just remember you can only install software from one of the aforementioned methods at a time.

---

### Post by Diabolis on 2008-03-25
**Also, make sure you're not trying to run Synaptic and automatic updates at the same time. And make sure Synaptic isn't open if you are typing apt-get something. You can't do 2 Apt things at once.**

This thread should be merged.

---

### Post by aysiu on 2008-03-25
Here's a quick run-down on what's happening.

The package manager (APT) manages the installation and removal of software packages. It installs software and uninstalls software. You don't need to separately download an installer file as you did in Windows or Mac. The package manager finds the installer file and takes care of all of that for you.

The graphical programs Update Manager, Synaptic Package Manager, Add/Remove, and Adept Package Manager are all frontends for the same behind-the-scenes package management process. The terminal commands *apt-get* and *dpkg* are also a way to access the package manager.

Only one program can access the APT process at a time. So you cannot run *dpkg* and have the Update Manager open at the same time.

To temporarily assume superuser (or administrative privileges), you add the word *sudo* to a command. 

**No superuser privileges**: ```
dpkg --configure -a
``` **Superuser privileges**: ```
sudo dpkg --configure -a
``` For further reading:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by munch3 on 2008-03-25
all worx well now tnx all

---

### Post by munch3 on 2008-03-25
all worx well now tnx all

---

### Post by blithen on 2008-03-25
Make sure you don't have another terminal open with it running, or synaptic OR add/remove. Make sure you have none of these open then try the command.

---

### Post by Diabolis on 2008-03-25
You didn't need to start this thread, several people gave you the answer on the other one. Seems like you are posting just to get more beans.

---

### Post by Paqman on 2008-03-25
You need to shut Synaptic, Add/Remove and the Updater, if any of them are open. The  try that command again.

---

### Post by forrestcupp on 2008-03-25
> **munch3 said:**
> all worx well now tnx all

Tell us how you got it working for future reference when people have the same problem.

---

### Post by bapoumba on 2008-03-26
Threads merged.

---

