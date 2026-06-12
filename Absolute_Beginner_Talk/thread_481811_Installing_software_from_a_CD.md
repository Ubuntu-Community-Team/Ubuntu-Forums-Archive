---
title: "Installing software from a CD"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-22
One of my friends just got a new comp that we want to try Ubuntu on. The thing is, it has no internet access. The only thing he needs (we think) is Wine, so he can play Star Craft. I just downloaded a .deb from the Wine site, 

1)  so can I just burn this as a data cd and it will install for him? 

2) Are their extra dependencies I need to worry about?

3) How can I install it so that synaptic tracks it, just in case he gets internet in the future?

---

### Post by Seisen on 2007-06-22
Here are the dependicies you will need for wine.

[http://packages.ubuntu.com/feisty/otherosfs/wine]("http://packages.ubuntu.com/feisty/otherosfs/wine")

---

### Post by FleetAdmiral74 on 2007-06-22
So if I dl the wine package from the link under all the dependencies, will that include all of them? Or must I install them manually...

when I click on one dependency, it just pops up with dependencies for that dependency...

---

### Post by Seisen on 2007-06-22
If those files are on the Ubuntu cd, if not than you have to download at least the ones with the red dots and install them along with wine.

---

### Post by FleetAdmiral74 on 2007-06-22
but almost every red dot has more red dots when I click them...there HAS to be a better way lol.

or is that really how bad it is w/o internet?

---

### Post by FleetAdmiral74 on 2007-06-22
Bumpity bump

I am going over soon, so was hoping to get a quick response.

---

### Post by Seisen on 2007-06-22
You might be able to pull all of the files off of the Ubuntu cd itself, which means you need to set it as the only repository.

---

### Post by FleetAdmiral74 on 2007-06-22
Alrighty. How do I go about setting the cd as a repository?

thanks for sticking with this, I do appreciate it.

---

### Post by kevdog on 2007-06-23
To set up a cd as a repository:

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ****** <--Whatever package name you want.  

Ive never tried to load a bunch of dependencies from CD, but I think if you have them on CD, aptitude should find them.  Let me know!

---

### Post by AnRa on 2007-06-23
You may find [APTonCD](http://aptoncd.sourceforge.net/) useful! ;)

---

### Post by FleetAdmiral74 on 2007-06-23
Wow, thanks for the APT link and how to set up the repositories, does not look too hard.

btw, I just found out that his comp only has like 128megs of ram. Is xubuntu recommended at this point, or resort to fluxbuntu? And if the latter, is it officially supported or anything like Edubuntu is?

---

