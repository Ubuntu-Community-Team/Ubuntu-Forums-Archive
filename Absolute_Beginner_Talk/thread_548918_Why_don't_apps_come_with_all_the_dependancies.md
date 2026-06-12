---
title: "Why don't apps come with all the dependancies?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by its_toby on 2007-09-11
Wouldn't it make more sense to write all apps with all the necessary dependencies so that when the app is loaded there would be no need to spend countless hours looking for the depends the app needs.  Then if your distro already has the depends it doesn't have to load them.  This would make things much easier don't you think, or amy I missing something?

Thanks

---

### Post by reckless2k2 on 2007-09-11
huh...are you new to a debian/ubuntu distro? apt/synaptic is probably the best package manager that handles issues like that. this is not a RPM distro and even nowadays they are much better than even a year ago. are you installing from the source? if so, dump it for apt. you might be doing it the hardway. it wouldn't consider it the wrong way....definitely the hard way though,

---

### Post by its_toby on 2007-09-11
No, I understand that, I guess my point is, I recently downloaded 4 differnt pieces of software and none of them work because they lack dependencies.  I know that apt rocks but when you have to download your apps to a cd or usb drive and then install them to the kubuntu sys then it becomes a big pain in the !@#$.  If the applications were bundled with all the needed depends then those who don't have access to a continuous broadband could have the opportunity to get new applications without all the pain and suffering the comes with dial-up or no internet access at all

---

### Post by tyggna1 on 2007-09-11
Dude, the dependencies are different in Kubuntu than in Ubuntu--that's why you're having issues.  And transferring over a CD is not the typical Linux way--repositories are always best.

---

### Post by misfitpierce on 2007-09-11
Yes in Kubuntu you may find yourself searching through packager handler to find recently installed program only to right click and click install again so it can get dependancies. In ubuntu however gnome installer auto downloads and installs dependancies as it should be. I think the system is fine.

---

### Post by its_toby on 2007-09-11
So Kubuntu doesn't have the same backend as Ubuntu? I thought that it was just the desktop.  Anyway, I understand what your saying, but if Linux is going to be for the masses then it has to be available to all in all different situations, not just repositories that need to be accessed online with highspeed connections.  Don't get me wrong, I'm having a blast with Linux, I'm just saying that more options means more people.

---

### Post by reckless2k2 on 2007-09-11
oh now i got you its_toby. sorry i misunderstood. that all can be resolved by using pc-bsd or mac.

hahaha...seriously...a downloaded package is self-contained. a wonderful function. klik does this as well but not as good. might be better...not sure but all that plus goodness though is outweighed by the fact that those packages are not very robust. meaning that klik doesn't have everything you need or most people do. mac and pc-bsd fall into this trap as well. pc-bsd is hot though. maybe they have enough. it's not terribly hard to make a pbi single installer package either though if you need a custom. 

check out pc-bsd...might be what will work for you.

---

### Post by danny joe ritchie on 2007-09-11
its_toby 
Do you have access to a machine with a fast internet connection? If so download a 7.04 iso and burn it to a disk ,use this instead of 6.10 that way your modem will work and you will be able to access the repositories!

Or did you get your modem to work with 6.10?

---

### Post by Neobuntu on 2007-09-11
The answer is, some do. But it promotes bloat. It's reinventing the wheel. Each time; in many cases.

---

### Post by aysiu on 2007-09-11
If I had dial-up or no internet connection, I would definitely *not* use Ubuntu.

---

### Post by lisati on 2007-09-11
> **its_toby said:**
> Wouldn't it make more sense to write all apps with all the necessary dependencies so that when the app is loaded there would be no need to spend countless hours looking for the depends the app needs.  Then if your distro already has the depends it doesn't have to load them.  This would make things much easier don't you think, or amy I missing something?

Thanks

Some methods are easier for some people than others.....
The trouble with including ALL the dependencies is that the package someone puts together could easily include stuff by other people that is quickly outdated.

---

### Post by BrendanM on 2007-09-12
Plus, including all the dependencies in every software package would make those packages bigger and slower to download on slow connections. You'd wind up downloading the same things over and over again. Part of the *nix development philosophy involves making small pieces of software that do one thing well. Then other programs can just call existing apps rather than implementing the same functionality over and over again.

---

