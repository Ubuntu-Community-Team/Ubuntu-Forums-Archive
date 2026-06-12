---
title: "Skype install on Kubuntu and Ubuntu"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-03-10
How do I install Skype on Ubuntu and Kubuntu, and is there alinux version, or do I have to install via Wine

---

### Post by Duck2006 on 2008-03-10
In synapic Package Manager you can find Skype

---

### Post by FuturePilot on 2008-03-10
There's is a Skype package in the Medibuntu repos.
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get install skype
```

---

### Post by CIZZO20 on 2008-03-12
I don't know what vers is on there but you can download it from here
[http://www.skype.com/download/skype/linux/beta/choose/](http://www.skype.com/download/skype/linux/beta/choose/)

This beta vers is much much better then the current stable one. 
The problem where skype takes over your sound card was fixed and also webcam was added

---

