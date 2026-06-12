---
title: "Where to get 'make'"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by stil on 2007-07-28
easy question. ive tried to install wine. apparently i need 'make' to help me do this. i don't have 'make'. ive looked through the package manager, searching for 'make', but not found what im looking for. considering the name of the tool im looking for, google has turned into a bit of a nightmare. trying to formulate a search for downloading 'make' for linux. is it part of a set of commands with a different name? :confused:

---

### Post by walkerk on 2007-07-28
in terminal:
```
sudo apt-get install make
```

---

### Post by Mornedhel on 2007-07-28
If you need make, it's included in the build-essential package which you'll probably need entirely should you compile something. However, Wine is in the repositories as well.

---

### Post by Bachstelze on 2007-07-28
> **stil said:**
> easy question. ive tried to install wine. apparently i need 'make' to help me do this. 

No, you don't. *make* is usually used to compile programs from source, which is not how you should install WINE. I suggest you have a look at this to learn how to install software in Ubuntu.

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by stil on 2007-07-28
I should have mentioned, the lan isnt working on this machine. no internet. is that command going to install from the internet or a repository/liveCD?

---

### Post by rich.bradshaw on 2007-07-28
Everything is from the internet.

To install wine:

sudo apt-get install wine

. Don't bother compiling from scratch using make, it's a complex and unnecessary way of doing things!

---

### Post by Mornedhel on 2007-07-28
Oh.

Quite a different problem.

build-essential is still included in the install CD. Wine isn't, so you may want to download it manually from packages.ubuntu.com, then pray for all the packages it depends on to be included on the CD also (and Wine depends on quite a few packages, according to apt-cache).

---

### Post by stil on 2007-07-28
build-essentials.... that rings a bell.

ill grab wine from that site. i already have a tar from their website, thats how i got here.

---

