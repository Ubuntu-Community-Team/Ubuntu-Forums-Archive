---
title: "A tiny doubt with APT"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by kart3r on 2006-05-22
What kind of installation uses apt-get?It builds the binarie package?Sorry but i'm newbie around here.

---

### Post by Denis on 2006-05-22
APT downloads the deb packages from the server. These deb packages contain all the files, including binaries, of the program you want to install. 

So apt-get doesn't build anything, it just downloads programs and installs them (move the files to the right location).

---

### Post by kart3r on 2006-05-22
Ok thks a lot

---

### Post by kart3r on 2006-05-22
Can you explain me how do I install binaries and how do i install a program recompiling the source?

---

### Post by Klaidas on 2006-05-22
To compile from source, you will need build-essential package.
Then you type 
```
./configure
```
```
make
```
```
sudo make install
```
But most of the programs you need can be found on SYnaptic package manager, so you won't have to compile :)

---

### Post by kart3r on 2006-05-22
And how do I build-essential package?sorry but i'm really nerd about this :X

---

### Post by Klaidas on 2006-05-22
```
sudo apt-get install build-essential
``` :)
I recomment you reading:
[https://wiki.ubuntu.com/InstallingSoftware](https://wiki.ubuntu.com/InstallingSoftware) :)

---

### Post by kart3r on 2006-05-22
Thks :) I'm doing some work about ubuntu and i need to learn how to do this stuff and no one better then YOU (ubuntu comunity) to teach me hehehe

---

### Post by Kimm on 2006-05-22
if you want to recompile a package found in the repositories (programs that you download and install using apt-get) you can do this:

sudo apt-get build-dep <package>
sudo apt-get -b source <package>

---

### Post by nanotube on 2006-05-22
you might also find helpful the second link in my sig, it details the various ways of installing software on ubuntu.

---

### Post by kart3r on 2006-05-22
Kimm and if I had the source in my computer how do I do that?

---

### Post by nanotube on 2006-05-22
[QUOTE=kart3r]Kimm and if I had the source in my computer how do I do that?[/QUOTE]
heh, check the install guide in my sig - it tells exactly how to install from source. :)

---

