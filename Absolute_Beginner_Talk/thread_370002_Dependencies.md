---
title: "Dependencies"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by ColinP on 2007-02-25
I am installing an HTTrack (i386 deb. file) . Gdebi states an dependency error i.e. libc6.   Synoptic P.M. states that this file is installed !   I would appreciate some advice here.  Please bear in mind that I am a learner with still more to learn.

---

### Post by DougieFresh4U on 2007-02-25
You could try **sudo apt-get -f install** & also **sudo dpkg --configure -a**. Worth a shot.  :)

---

### Post by ColinP on 2007-02-25
Thanks,  first result.  Please note that the package is on the desktop

olin@colin-desktop:~$ sudo apt-get -f install httrack_3.40.4-3.1_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package httrack_3.40.4-3.1_i386.deb

I will now try your second suggestion.

---

### Post by DougieFresh4U on 2007-02-25
> **ColinP said:**
> Thanks,  first result.  Please note that the package is on the desktop

olin@colin-desktop:~$ sudo apt-get -f install httrack_3.40.4-3.1_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package httrack_3.40.4-3.1_i386.deb

I will now try your second suggestion.
Did you run **sudo apt-get update** & **  sudo apt-get -f install**

---

### Post by ColinP on 2007-02-25
No luck there I am sorry to say !

---

### Post by Rui Pais on 2007-02-25
> **ColinP said:**
> Thanks,  first result.  Please note that the package is on the desktop


That means that you download the package from somewhere... probably from a debian repository. 
Most of the time they are not compatible with this or that ubuntu version..


You just need to do:
```
sudo apt-get install httrack
```

---

### Post by mcduck on 2007-02-25
> **ColinP said:**
> Thanks,  first result.  Please note that the package is on the desktop

olin@colin-desktop:~$ sudo apt-get -f install httrack_3.40.4-3.1_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package httrack_3.40.4-3.1_i386.deb

I will now try your second suggestion.
Try with 'sudo apt-get -f install' only. The package name doesn't belong to this command.

You can't use apt-get to install packages you have downloaded yourself. (packages that are allready on your computer are installed with 'dpkg -i <packagename>' or using Gdebi). Apt-get and Synaptic only install packages from repositories.  Try with only 'sudo apt-get -f install'.

Anyway, id Gdebi says that there is a dependency problem with libc6 but you know that it's installed it's most likely a problem with the version of libc6. You should check what version you have and what version that package you are trying to install needs ;)

---

