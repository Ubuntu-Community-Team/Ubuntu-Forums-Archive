---
title: "FLuxbuntu/Ubuntu install LIveCD WTF? *need help asap*"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by ritterrav on 2007-09-05
Ok, my friend has a old PC, and the Ubuntu 7.04 live CD is to much for it to boot up i guess, it usually hangs at 15%.  So i said install fluxbuntu, it is lighter and runs better on old PC's. When he installs it, its like japanese meets egyptian, and i cant really figure it out myself, its not that diff, but then again it is in its own way. so i say lets see if we can install ubuntu from the live cd while in Fluxbuntu, so we can get to a more common linux were we feel normal..

But i dont know how i can install Ubuntu from the liveCd while in Fluxubuntu? So if theres anyway to do this, a step by step would be great.  I know Xubuntu is supposedly lighter, but we dont have that livecd and i can just install xubuntu later. 

Or if i can be told how to make ubuntu stop hanging at 15% that would be good also. 

thank you very much.

---

### Post by WebSiteGuru on 2007-09-05
Alternate CD is what you need to use for Ubuntu. TEXT base installation for those real slowwwww computer.... ;)

---

### Post by mocoloco on 2007-09-05
If you have a fast internet connection you can install either.   Open a terminal, or do Ctrl+Alt+F1 and do 
```
sudo apt-get install xubuntu-desktop
```
or
```
sudo apt-get install ubuntu-desktop
```
Then sit back and wait for a while :)

---

### Post by WebSiteGuru on 2007-09-05
> **mocoloco said:**
> If you have a fast internet connection you can install either.   Open a terminal, or do Ctrl+Alt+F1 and do 
```
sudo apt-get install xubuntu-desktop
```
or
```
sudo apt-get install ubuntu-desktop
```
Then sit back and wait for a while :)

I dont think that can be done. I think this is  a new install.

---

### Post by sumguy231 on 2007-09-05
You can. Go to a terminal and type:
```
sudo apt-cdrom add
```
Follow the instructions.Then do this:
```
 sudo apt-get update
sudo apt-get install ubuntu-desktop
```

Butif you have a working internet connection, you can go ahead an install Xubuntu without Ubuntu with:
```
sudo apt-get install xubuntu-desktop
```

Now wait a really long time.

---

### Post by ritterrav on 2007-09-05
But the thing is that he has a Linksys wireless adapter hooked up to his PC, so how would i  install that in Fluxbuntu then hit the sudo what ever...


ALSO, can i get a link to that ALTERNATE CD to install Ubuntu 7.04 in a text based installation?

---

### Post by WebSiteGuru on 2007-09-05
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) << Same link there is a check option for Alternate CD at the bottom by the Green Start Download Icon.

---

### Post by mocoloco on 2007-09-05
> **WebSiteGuru said:**
> I dont think that can be done. I think this is  a new install.

Doesn't matter.  If you have enough of an install to get to a terminal you can then install the default (X/K)Ubuntu setup through apt (or a frontend like synaptic).  As long as the same Feisty repositories are setup in /etc/apt/sources.lst.
apt + internet = a beautiful thing :)

---

### Post by WebSiteGuru on 2007-09-05
> **mocoloco said:**
> Doesn't matter.  If you have enough of an install to get to a terminal you can then install the default (X/K)Ubuntu setup through apt (or a frontend like synaptic).  As long as the same Feisty repositories are setup in /etc/apt/sources.lst.
apt + internet = a beautiful thing :)

Even with the fresh install? Just Curious. Inquiring mind wants to know, just incase I need to use it. Got an old computer sitting in the closet that I want to load up Ubuntu (later).

---

### Post by mocoloco on 2007-09-05
> **ritterrav said:**
> But the thing is that he has a Linksys wireless adapter hooked up to his PC, so how would i  install that in Fluxbuntu then hit the sudo what ever...


ALSO, can i get a link to that ALTERNATE CD to install Ubuntu 7.04 in a text based installation?

Do you already have an internet connection? Do
```
ping -c 4 www.ubuntu.com
```
If not, search these forums for how to setup your linksys adapter.
If you do, then it doesn't make sense to download another CD (~700MB) when with apt you'll only download what you need (maybe 200-300 MB).

---

### Post by mocoloco on 2007-09-05
> **WebSiteGuru said:**
> Even with the fresh install? Just Curious. Inquiring mind wants to know, just incase I need to use it. Got an old computer sitting in the closet that I want to load up Ubuntu (later).

Oh yeah.  You can do a command-line only install, then add all the desktop packages at any time with those 3 meta-packages (ubuntu-desktop, kubuntu-desktop, xubuntu-desktop).

If you want to play around and don't like fluxbox, I like icewm better for older machines.  At one time I was working on a setup using icewm, pcman file manager, and some lightweight tools, but it ended up running about the same as XFCE (Xubuntu), and wasn't as easily configurable, etc.  If you want a full desktop experience on an old machine, Xubuntu is your best bet in my experience.

---

### Post by WebSiteGuru on 2007-09-05
> **mocoloco said:**
> Oh yeah.  You can do a command-line only install, then add all the desktop packages at any time with those 3 meta-packages (ubuntu-desktop, kubuntu-desktop, xubuntu-desktop).

If you want to play around and don't like fluxbox, I like icewm better for older machines.  At one time I was working on a setup using icewm, pcman file manager, and some lightweight tools, but it ended up running about the same as XFCE (Xubuntu), and wasn't as easily configurable, etc.  If you want a full desktop experience on an old machine, Xubuntu is your best bet in my experience.

Thanks for the info, I am definately be running Xubuntu for sure on that system. Just want to get my main computer up and operational first (if you know what I mean ;))

---

