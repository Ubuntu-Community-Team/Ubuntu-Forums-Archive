---
title: "Installing new beta Pan newsreader"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by confused57 on 2006-04-10
There's a new beta version of Pan available at:

[http://pan.rebelbase.com/download/](http://pan.rebelbase.com/download/)

I've downloaded the 0.92 deb file for Ubuntu and was wondering if I needed to remove the version I have installed from the Breezy repositories before trying to dpkg the deb file.  There are 12 dependencies also installed with the Breezy repo version, and I was wondering if I needed to leave the old version for the dependencies(if that might be a viable option).  Or would be better to remove the old version, use "sudo dpkg -i ....deb", then "sudo apt-get -f install" to install the needed dependencies.  Supposedly the new beta(unstable?) version uses much less memory and has several bug fixes.  It's mainly for my own edification and learning experience on an old test computer(500 MHz, 256 ram), on which the Breezy repo pan version is rather slow.   The Breezy version is plenty fast on my main computer(2.93 GHz, 1GB memory).  Thanks!

---

### Post by dcstar on 2006-04-10
[QUOTE=confused57]There's a new beta version of Pan available at:

[http://pan.rebelbase.com/download/](http://pan.rebelbase.com/download/)

I've downloaded the 0.92 deb file for Ubuntu and was wondering if I needed to remove the version I have installed from the Breezy repositories before trying to dpkg the deb file.  There are 12 dependencies also installed with the Breezy repo version, and I was wondering if I needed to leave the old version for the dependencies(if that might be a viable option).  Or would be better to remove the old version, use "sudo dpkg -i ....deb", then "sudo apt-get -f install" to install the needed dependencies.  Supposedly the new beta(unstable?) version uses much less memory and has several bug fixes.  It's mainly for my own edification and learning experience on an old test computer(500 MHz, 256 ram), on which the Breezy repo pan version is rather slow.   The Breezy version is plenty fast on my main computer(2.93 GHz, 1GB memory).  Thanks![/QUOTE]
I installed this beta version the other day and promptly uninstalled it, it had limited functionality on my system and didn't pick up my existing settings at all.

In other words, for me it didn't matter how fast this was supposed to be, it just didn't give half the required functionality that the working version does.

I think I'll wait for them to sort out these issues.

---

### Post by confused57 on 2006-04-10
Thanks for the reply.  I'm with you, think I'll wait for the stable version after they work some(most) of the bugs out.

---

