---
title: "uninstalling/remove all files associated with something!!!"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-07-12
I installed ndiswrapper and got the driver to work and everything but for some odd reason i went to continue my wireless configuration and in the terminal it says ndiswrapper is not installed! but i know for sure it was i have loads of out put and i was able to see wireless connections the other day.  I have decided to do a fresh install and but was wondering what the proper way of removing a program is.  there's the apt-get remove, but are there other ways/ how do u complete remove alllll files associated with something!  so far the only way i've tought of is to search ndiswrapper and just delete them but it could ahve created countless other files that don't contain ndiswrapper in the filename!  that's my only beef with ubuntu is i find it hard to keep track of what is installed and when you remove things how much extra crap is left behind.  Any help would be greatly appreciated.

Thanks, Alain

---

### Post by FleetAdmiral74 on 2007-07-12
Holy crap, thats a lot of info.

Its funny you say that, I LOVE ubuntu for how it tracks stuff. How did you install it in the first place?

Go to system - administration - synaptic. If you install and uninstall there, it tracks EVERYTHING automatically for you. I live by synaptic.

believe me, what you point out as your main beef is one of Linux's and Ub's STRONGEST advantages in my PoV. Just got to use it :)

---

### Post by eldepeche on 2007-07-12
sudo apt-get remove --purge [package]

---

