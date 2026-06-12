---
title: "help on unbuntu-desktop wanting to be removed"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by neilw on 2006-07-19
Hello,
I have installed a package (gnucash) to try out but don't want it. When I go to remove it, it tells it a dependency 'ubuntu-desktop' will also be removed.

This doesn't sound right to me as it sounds like a system package and the description says it is used for package installation.

Assuming this is a required package, how do I get rid of software as this was also mentioned when I tried to remove Mozilla browser.

Any help would be appreciated :)

Neil.

---

### Post by Sandlst on 2006-07-19
The ubuntu-desktop package is a meta package that depends on all the packages in the default ubuntu installation.  There is no data in the package itself, when you install it the package simply installs all the default stuff along with it since it depends on the default stuff.  It can be removed without fear.

---

### Post by neilw on 2006-07-19
thanks, I'll do that. Maybe it should be called something less scary ;)

---

### Post by SkyNet2029 on 2006-07-19
Just to play it safe (and since the base meta-packages are used for upgrading purposes too ) I tend to reinstall that meta-package promptly after whatever offending program is removed. On the package descriptions (In Adept or Synaptic, Aptitude as well ) it clearly states wether or not you actually need a certain meta-package laying around forever, for future use and what-not.
But no, removing these when performing package maintenance should not hose your installation. Besides, even if it does turn out that you need it later on  (as another package's dependency, say ) , the dpkg or apt will prompt you as to this so that you can correct it.

---

### Post by richbarna on 2006-07-19
> **neilw said:**
> thanks, I'll do that. Maybe it should be called something less scary ;)

Lol, I remember the first time it happened to me. You may have a point there. Maybe they could call it "everything-on-your-computer" :)

---

### Post by neilw on 2006-07-19
I'm happy now it won't cause any damage :)

This all came about because after using the excellent Automatix (I now have most things I need working) it installed a lot of stuff I explicitly said I didn't want.

Digressing slightly, one thing that has made me wonder about the ubuntu system is that it doesn't even install gcc/g++/etc. Even microsoft ship a compiler with their stuff now ;) Fair enough it's because it's aimed at people who probably don't want to develop software, but in that case, why ship gcc documentation and gdb.

Any thanks, I'm sure in time I'll be able to contribute rather than ask questions.

---

### Post by SteveHoffmanUK on 2006-07-19
Neilw

Thanks very much for asking your question. I, too, was so alarmed at the idea of ubuntu desktop being uninstalled that I have left a package on my system that I no longer want. I guess I can now remove it.

But it would save a lot of grief if something could be done to Synaptic to send out a less alarming message.

---

### Post by 3rdalbum on 2006-07-19
The package description should be changed to make it a little clearer.

As for the compilers and things, you can install the package "build-essential" to get the compilers and libraries. I think it's not installed by default for a good reason: Discourage newbies from trying to compile software and then saying "It's too hard to install software on Linux". However, I don't know why it ships with the GCC documentation :-)

---

