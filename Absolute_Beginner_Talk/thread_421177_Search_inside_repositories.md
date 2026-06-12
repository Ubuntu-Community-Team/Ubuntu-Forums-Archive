---
title: "Search inside repositories"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by doomster on 2007-04-24
hello there:)

first of all i would like to congratulate you all for the great help you offer through your forums.even 
for us, new users of Ubuntu, and generally unix systems, with forums like this, managing a linux 
box becomes fairly easy:)

I am using Ubuntu Feisty 7.04.In order to install new software ive found handy to use apt-get from console.
Is there any way to search through repositories for certain software-title , with the use of console?

thanx in advance for your help

---

### Post by Rinzwind on 2007-04-24
apt-cache search atari

tries to find a package atari.

---

### Post by doomster on 2007-04-24
thanx alot for your quick respond :)

---

### Post by hyperair on 2007-04-24
These commands may come in useful as well:

apt-cache show atari
shows the description among other things for package atari

apt-cache policy atari
shows the version of package atari installed on your computer, the candidate version to be installed on your computer (will be installed via sudo apt-get upgrade or by sudo apt-get install atari)

---

