---
title: "Install ubuntustudio on ubuntu"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Steinarlundemo on 2007-06-10
Hi

I have just downloaded ubuntustudio and I was surprised that it was an "own" distro. But that didn't stop me. I started up synaptic package manager and chose "add cd".

It started good, but I got an error message, and it wouldn't continue. 

What should I do to add the studio to my current ubuntu 7,04 package?

Sorry for my crappy english ;)

---

### Post by NeoLithium on 2007-06-10
I think you should be able to set up the repos' as their page says ( [http://www.ubuntustudio.com/downloads](http://www.ubuntustudio.com/downloads) ) and install the packages listed a little farther down that page, though I haven't tried this method (I installed through CD)

---

### Post by Stinger on 2007-06-10
Hi ,
I'm running ubuntustudio , I upgraded from Feisty using this guide :

[UpgradingFromFeisty]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty")

Only hickup I had was the nvidia driver not working but I solved that booting into the old feisty kernel ,  installing the nvidia packages for the low latencety ubuntustudio kernel and rebooting. 

Hope it helps

---

### Post by ElEdwards on 2007-06-10
I also upgraded to Studio using the same link as Stinger.... but now my laptop's network card is no longer seen.  I can reboot to the Ubuntu 7.04 (where I am right now) and my network card is seen.

Any ideas how I can make my card be seen in Studio?

Thanks :)

---

### Post by Stinger on 2007-06-12
Maybe it's because your network card depends on the restricted-moduls package , if so try this , boot into 7.04 Feisty , if you are not already there, open a terminal and do this

```
sudo apt-get install linux-restricted-modules-lowlatency linux-restricted-modules-2.6.20-16-lowlatency
```

and reboot into your lowlatency kernel (should be default)
this would bring you the newest restricted-modules matching your kernel.

Hope it helps.

---

### Post by ICUR2Ys on 2007-06-12
I installed ubuntu studio by going to the site given by NeoLithium.  I entered the two commands just under the heading ubuntu studio repo.  After that the install was done by synaptic.  All very clean and easy for on this system.

---

### Post by ilmuikhlas on 2007-08-12
what is the different between original ubuntu and that ubuntustudio?
can i just install all the software included in ubuntustudio on my ubuntu feisty from repository?
then i currently use ubuntu feisty 64 bit version because i am intesrested in using 64 OS....
does ubuntu studio have 64 bit version too??

sorry for my crappy english to... im not englishman:):)

---

