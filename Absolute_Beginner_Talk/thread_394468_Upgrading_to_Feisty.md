---
title: "Upgrading to Feisty"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Error47 on 2007-03-26
Hello, I am a beginner Ubuntu/Linux user. I like the latest updates, should I upgrade to the newer version. I am now running 6.10 . I don't even know how to upgrade, I'm sure [this]("http://onlyubuntu.blogspot.com/2007/03/upgrade-ubuntu-610-edgy-eft-to-ubuntu.html") would help me. Hearing that it is not stable and all, is there many problems with it?  Will    I loose all my programs, mounted hard drives, beryl, or any other configurations if I perform this upgrade?   Thanks.

---

### Post by murlosad on 2007-03-26
Feisty is still in testing, if you are a new user and this is your primary machine, I wouldn't upgrade just yet. If you are willing to experiment and not worried about possibly losing some information, download the cd and go for it. I've been using the latest release of feisty for about a week now without any problems. But I also started from a fresh install, upgrading may work differently and it can also depend on your hardware.

But, if you want to keep learning while not risking your current installation and settings it may be best to stick with what your using for now. If you want to experiment or just like to have the latest and greatest, dive right in.

I've lost track of how many different versions and distributions I've tried over the last 6 or so years just for the heck of it. As long as you don't have anything that you can't replace on your harddrive, what's it gonna hurt?

---

### Post by zvacet on 2007-03-27
Before you start to upgrade download Apt on CD.Thet is tool wich will save everything you have in var/cache/apt/archives .In other words everything you ever download or install with synaptic or apt-get.That is just to be in position to restore Edgy if something goes wrong with upgrade to Feisty.
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

upgrade command is 
```
update-manager -d
```

---

