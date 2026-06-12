---
title: "[SOLVED] My apt-get seems to be broken..."
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Jeezus on 2008-01-23
jeezus@MacWheezy:~$ sudo apt-get install automatix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package automatix
jeezus@MacWheezy:~$ sudo apt-get install libxine-extracodes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libxine-extracodes

Everytime I try to install something through the terminal it tells me that it can't find the package...
do I need to be more specific in the packages I ask for? version numbers or something? It's getting kind of frustrating... =(

---

### Post by aysiu on 2008-01-23
> **Jeezus said:**
> jeezus@MacWheezy:~$ sudo apt-get install automatix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package automatix
jeezus@MacWheezy:~$ sudo apt-get install libxine-extracodes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libxine-extracodes

Everytime I try to install something through the terminal it tells me that it can't find the package...
do I need to be more specific in the packages I ask for? version numbers or something? It's getting kind of frustrating... =(
Do you understand how *apt-get* works?

*apt-get* references a file called /etc/apt/sources.list, which specifies what online software repositories to install software from.

If your /etc/apt/sources.list does not list a repository that has Automatix, you won't be able to *apt-get* Automatix. Same goes for *libxine-extracodes*, which I don't even think is a real package.

Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by por100pre1 on 2008-01-23
Automatix2 is NOT available in the repositories. I don't recommend you to use it. What do you need to install?

---

### Post by smurphy_it on 2008-01-23
I don't see them in my list so they are probably not in the repositories.  These might be 3rd party or unsupported ones.

I'd have to make the change and reload the repositories to even see them.

As long as you have an internet connection you should be able to grab packages from the repositories.

---

### Post by aysiu on 2008-01-23
This link may help, too:
[http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)

---

### Post by Jeezus on 2008-01-23
libxine-extracodecs was something I found just recently on the forum as a possible solution to my online video troubles. It's an alternative to gstreamer... or at least that's what it was made out to be, but I figured I'd try.

I understand how apt-get works now, so where do I find more repositories?

---

### Post by aysiu on 2008-01-23
I don't think *libxine-extracodecs* exists for Ubuntu 7.10 (it did for older versions).

For more repositories, try [this](http://www.psychocats.net/ubuntu/sources#key).

---

### Post by Jeezus on 2008-01-23
Thanks!

---

