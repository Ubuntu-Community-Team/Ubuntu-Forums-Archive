---
title: "My Ubuntu Beef - or what am I doing wrong?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Tweek84 on 2006-09-02
Something has bothered me ever since I started with Ubuntu back in october.

Ubuntu is easily the nicest Linux distro I've used, the most refined, good base packages, and of course like any linux - extremely customizable.

Between the Deb packages and apt-get installation of software is quite easy.

However this is where my frustration comes in.

libxine-extracodecs

libxine-extracodecs is the bain of my existance. According to the ubuntu wiki 
libxine-extracodecs is required for mp3 playback with amarok, and although I"m using Enlightenment E17 I prefer Amarok as my media player. 

Now, anyone who has tried to install this package in the normal manner knows what I'm about to say.
apt-get install libxine-extracodecs will return a somewhat cryptic message about the package not being available.

The package opera returns similar results, and indeed I have found this same message for a number of packages.

Now i realize it's as easy as finding the package online and installing it with dpkg but that's a pain in the butt especially frustrating simply because the message simply doesn't really give any indication of what's going on.


Now that I've ranted I'm actually hoping someone comes by and tells me I'm an idiot and missing a repository or something.

---

### Post by taurus on 2006-09-02
Do you have both universe & multiverse enable in /etc/apt/sources.list???

---

### Post by meborc on 2006-09-02
sometimes the package name is not the same... ahh.. how do i explain... lets say you need something like PACKAGE but acctually it is PACKAGE.1.10.12 ... with version name... so if you get an error that that package is not available, try

```
apt-cache search PACKAGE
```

then you will see what comes up... :wink:

---

### Post by Tweek84 on 2006-09-02
Aha! Good, it was just me.

I was missing two multiverse repos.

I've had this issue with way more than one install.

I feel quite foolish but I"m glad it was just me!

Thanks :)

---

