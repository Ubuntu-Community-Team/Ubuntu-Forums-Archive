---
title: "Doing full install of gutsy but restoring apps from fiesty"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by PetePete on 2008-01-15
i want to install gutsy (soonish) but dont want to have the hassle of re-installing all my packages which i've got installed.
Now i could upgrade, but due to various reasons which im not going to go into im not. and need to full install.

the method of running 'dpkg --get-selections > packages-installed' on my system before the install and saving this file (to say usb pen)

then once gutsy installed, I run dpkg --set-selections < packages-installed 
would this work? Ive done this before when reinstalling fiesty (from fiesty)

Im guessing id have to go through the file 'packages-installed' and remove any library's and kernel related stuff just to leave apps, then afterwards run a missing dependecy check to install require missing library's .

any easier way of doing this?

---

### Post by philinux on 2008-01-15
This may help you.

[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)

The same principles apply.

---

### Post by PetePete on 2008-01-15
ta for that, I assumed that id need to remove librarys due to conficts and such.

anyway, good to know i dont.

Thanks.

---

### Post by jrusso2 on 2008-01-15
I have had good results using the upgrade manager.  First I will rem out any non-stock repositories I have added such as automatix.

Then run the upgrade manager and when it asks if I want to keep  a configuration I will answer yes.  You kind of have to keep an eye on it while its running and keep the details window open.

---

### Post by PetePete on 2008-01-15
yeah i can't fault the upgrade, worked flawlessly for edgy-fiesty , but I need to muck around with partition settings and stuff.

---

### Post by philinux on 2008-01-15
I did the upgrade from feisty to gutsy. It worked ok but not great. Had to do a clean install.

Put home on its own partition as well.

---

### Post by stchman on 2008-01-15
> **PetePete said:**
> i want to install gutsy (soonish) but dont want to have the hassle of re-installing all my packages which i've got installed.
Now i could upgrade, but due to various reasons which im not going to go into im not. and need to full install.

the method of running 'dpkg --get-selections > packages-installed' on my system before the install and saving this file (to say usb pen)

then once gutsy installed, I run dpkg --set-selections < packages-installed 
would this work? Ive done this before when reinstalling fiesty (from fiesty)

Im guessing id have to go through the file 'packages-installed' and remove any library's and kernel related stuff just to leave apps, then afterwards run a missing dependecy check to install require missing library's .

any easier way of doing this?

I have some scripts that will install a variety of popular apps in Gutsy.

[http://www.stchman.com/install_scripts.html](http://www.stchman.com/install_scripts.html)

---

### Post by PetePete on 2008-01-15
nice script, dont need all those apps but definatly going to download it and save for later editing/personalization :D

---

