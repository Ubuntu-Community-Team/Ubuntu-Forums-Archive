---
title: "cant update from mactel ppa"
date: 2009-10-15
forum: Apple Hardware Users
---

### Post by kpholmes on 2009-10-15
im trying to get updates for my macbook 5,1 from the mactel ppa but having trouble getting the GPG key.

im following these steps:[https://wiki.ubuntu.com/MactelSupportTeam/PPA]("https://wiki.ubuntu.com/MactelSupportTeam/PPA")

and this is what i get when trying to get verified after add the ppa to the sources list.


```
kevin@ubuntu-studio:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7A6BC20C4FE04DADD10837608DB7F87A2B97B7B8
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 7A6BC20C4FE04DADD10837608DB7F87A2B97B7B8
gpg: requesting key 2B97B7B8 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
kevin@ubuntu-studio:~$ 
```

---

### Post by proycon on 2009-10-16
I'm having the exact same problem now. Something wrong server-side perhaps?

---

### Post by kpholmes on 2009-10-20
ya i got over it and decided im going to run ubuntu in a virtual machine, the hardware support is alot nicer but its not as fast. :(

theres a trade off on both way you go. 

unless your a awesome programmer and and kink out the hardware bugs when running ubuntu from the hd. =D

---

### Post by Ravernomina on 2009-10-21
Sometimes the sever for Mactel is done to give the keys.... Its annoying i know try running the command later.

---

