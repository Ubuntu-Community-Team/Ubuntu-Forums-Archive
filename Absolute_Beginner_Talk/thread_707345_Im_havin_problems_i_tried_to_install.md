---
title: "Im havin problems i tried to install"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Kedster on 2008-02-25
i tried to re-install open office it failed and ever since then i get this messsage

E: openoffice.org-base: subprocess post-installation script returned error exit status 2
E: openoffice.org: dependency problems - leaving unconfigured

---

### Post by northern lights on 2008-02-25
Oye, how did you try to reinstall? Did you do a clean remove beforehand?

Maybe you've got two half-bred installations?

I'd recommend completely removing OpenOffice again, with all it's dependencies and then reinstalling. Use Synaptic, if you're not sure - OO is by default in your repos...

---

### Post by justleen on 2008-02-25
did you try to start it (open office, that is)?

try opening synaptic package manager, and select Fix broken
or
```
 
sudo apt-get check

```

Did you run a sudo apt-get update? what did that do?

---

### Post by djroadrash on 2008-02-25
its telling u there are dependency problems, that i think means u are trying to download or downloaded a upgrade that is not compatible quite with your installed sistem, what ubuntu are u running and whats on your etc/apt/sources.list, try what justleen said go to synaptic and completly remove it. then close synaptic and open a terminal, get root privileges or use ```
sudo apt-get update
```
then
```
sudo apt-get install openoffice
```

that should get rid of the badly installed one and get u installed OO.

there is also a way to use the terminal to purge the package instead of using synaptic

```
sudo apt-get purge openoffice
```

i believe that is the way to do it. Try synaptic and if it fails then do the purge command and see if that works.

about the etc/apt/sources.list am only mentioning in case u have two different repositories of ubuntu one newer than the other, that will cause the system to get a lot of dependency problems every time u download and install something.
good luck!

---

### Post by Kedster on 2008-02-25
i completly uninstalled and reinstalled and it worked

---

