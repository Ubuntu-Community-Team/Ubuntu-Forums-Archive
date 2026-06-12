---
title: "Repositories"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Nath on 2006-12-28
Hi ppl

I want to know what are repositories

Also please give me some information on how to use it to install  a program which I have downloaded the .rpm file from the net

---

### Post by PartisanEntity on 2006-12-28
Think of the repository as an online database of software and applications that are compatible with your curent version of Ubuntu.

You will find many different kinds of software and applications in the repository, you can browse through them by going to System > Administration > Synaptic Package Manager.

Also read this:
[https://help.ubuntu.com/community/CommonQuestions#head-b2f616ebcc51d91427733a29372697acac0f316a](https://help.ubuntu.com/community/CommonQuestions#head-b2f616ebcc51d91427733a29372697acac0f316a)

---

### Post by meng on 2006-12-28
Installing from an rpm is really a last resort. An rpm is a package created for installation on a different version of Linux, e.g. Fedora. The way to use this to install on Ubuntu is to use a program called alien to convert the rpm to a deb file, then install the deb file using dpkg. What you have to hope for is that the conversion doesn't make the package unusable on your system.

You are much better off installing from repositories (best), or downloading a deb file specifically for Ubuntu (still good), downloading a deb file not specifically for Ubuntu (still sometimes works) or else installing from the source code (usually works but you have to get your hands dirty). rpm should be a last resort.

---

### Post by anaconda on 2006-12-28
And if you are a beginner you should first learn how to use synaptic, and after that you can install alien, which can convert .rpm packages to .deb package, which is what ubuntu uses.

What program are you trying to install. My guess is that it propably is in ubuntus repositories already, so you wont need the .rpm -package. By the way rpm stands for redhat package management. (or similar) and they are meant (mostly) for redhat-linux or fedora core linux.

---

### Post by deadgobby on 2006-12-28
Here is a link to add extra repo's
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)
Gobby

---

### Post by batholith on 2006-12-28
Also, check out

[http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

it's a great place to learn and find some "how tos", if you not running Edgy, it also has links to previous versions of Ubuntu (Dapper/Breezy).

---

