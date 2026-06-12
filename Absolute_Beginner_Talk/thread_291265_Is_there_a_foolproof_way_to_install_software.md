---
title: "Is there a foolproof way to install software?"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by jefuchs on 2006-11-02
The standard method of ./compile etc doesn't seem to work for all programs.  Or at least I'm not savvy enough to know HOW to use it for all.

I want to install Firefox 2, and I see there's a how-to here, but I don't want to have to follow a different set of instructions for every different program I install.  

Is there a utility that looks at a downloaded program and automatically installs it based on what it finds?

Yes, I know about rpm and Synaptic, but some programs aren't accesible through those avenues.  If they are, please advise how.

kthnksbye

---

### Post by Paul41 on 2006-11-02
This doesn't answer you question about compiling, but Firefox 2 is already in Edgy. If you upgrade you will get it. Also for Firefox I don't think you have to compile the download you get from the Mozilla site. I think it is already compiled and ready.

---

### Post by tribaal on 2006-11-02
Hum well the stock version of firefox you get largely depends on what release of Ubuntu you're using.
If you run Edgy (Ubuntu 6.10), then you already have firefox 2 as the default browser.

If you run a previous version of Ubuntu, I'm pretty sure you can easily find a way to install firefox 2 on theses forums.

As for the foolproof way of installing/keeping software up-to-date, yes, synaptic or apt-get/aptitude command line tools are the best way by far. Make sure you check out the "universe" repositories as well, as they contain lots of software. They are community-maintained though, not maintained by Canonical, which can be a problem in commercial/professionaly situations.
Most users just enables theses repositories though, as the software they distribute is generally very stable and up-to-date.

Hope this helps you at all...

- trib'

---

### Post by Klaidas on 2006-11-02
the "./configure and etc" way is NOT the standard method. Standard method is > sudo apt-get install program

And yes, you're right, compiling might get (usually gets) nasty! 
So, what do you do if the program you are looking for is not in the repos? Well, it depends on the program. Some of them might be easily compiled (although I haven't found an easy compilable program for linux yet), ooor it might have a .bin file, oor someone might package it for you.

Anyway, I suggest you reading [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) :)

And to answer the original question... >  Is there a foolproof way to install software?
No

---

