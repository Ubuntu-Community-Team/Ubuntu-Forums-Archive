---
title: "aptitude vs apt-get"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by veelivar on 2006-04-18
Should I use aptitude instead of apt-get (or synamtic)?  I read eralier that it manages dependancies better but most guides seem to use apt-get, I wondered why?

Also if I should use aptitude instead can I just use it in the same way as apt-get when following a guide?

Sorry if this is a daft question.

Dan.

---

### Post by aysiu on 2006-04-18
[QUOTE=veelivar]Should I use aptitude instead of apt-get (or synamtic)?  I read eralier that it manages dependancies better but most guides seem to use apt-get, I wondered why?[/quote] Let's say you do ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` and then you do ```
sudo aptitude remove kubuntu-desktop
``` Aptitude will take away not only *kubuntu-desktop*--which is really not a package at all, but just a pointer to other packages--but also all the packages that were installed along with *kubuntu-desktop* (I believe it prompts you first, but I'm not 100% sure).

However, if you do ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
``` and then do ```
sudo apt-get remove kubuntu-desktop
``` only the pointer will be removed, not all the accompanying packages.

I think the reason apt-get is used so much is because... it's used so much. People see others recommending *apt-get*, so they in turn recommend apt-get.

> 
Also if I should use aptitude instead can I just use it in the same way as apt-get when following a guide? Yes.

---

### Post by earobinson on 2006-04-18
^^^ Blast I posted 2 slow, well I think i got it correct ne way ^^^

[http://www.ubuntuforums.org/showthread.php?t=37736&highlight=aptitude+apt-get](http://www.ubuntuforums.org/showthread.php?t=37736&highlight=aptitude+apt-get)

seems to me the only thing better it it handles the uninstalling of dependancies  better. I think ill stick with apt-get and synaptic for now.

---

