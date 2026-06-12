---
title: "Do I need *all* the updates 6.06 suggests?"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by fiver22 on 2006-08-02
Every 2 days or so Ubuntu tells me that there are updates to install...should I be allowing all these updates -or should I pick and choose the updates for the programs I am familiar with? -So far I've been installing everything: but I'm starting to wonder if I should be more selective.
(very new to Linux, btw)
Thanks for any advice/suggestions.

---

### Post by aysiu on 2006-08-02
After an official release, almost all updates are security updates. Unless you know better for sure, it's a good idea to install them.

---

### Post by wildseven on 2006-08-02
> **aysiu said:**
> After an official release, almost all updates are security updates. Unless you know better for sure, it's a good idea to install them.

i concur

---

### Post by fiver22 on 2006-08-02
Thanks for the replies, "wildseven", and "aysiu".
I'm humbled by the helpful-ness of the Ubuntu community: as a Linux newbie I will be spreading the word of Ubuntu.
Thanks so very much for your time!

---

### Post by eXisor on 2006-08-02
The update system tries to update everything you have installed, and this includes stuff you are not using, i.e. the old 386 kernel if you're using a 686 or k7 kernel. I suggest you remove everything you are not using anymore, and then do the updates.

---

### Post by Sweet Spot on 2006-08-02
Glad I found this thread, as I was going to create a similar one. My question is, when I absolutely know that I don't need the suggested updates, is there a way to turn off the notification for them ? I just installed 17 out of 19 updates, and decided that the two weren't necessary because I'm not really using the services (file sharing). 

But the notifiation icon is still there, and I'd like to get rid of it. Should I just uninstall those services totally, or can I jsut rid the icon another way ?

---

### Post by aysiu on 2006-08-02
If you don't want security updates for certain packages, I'd remove those packages. If you want older versions of particular packages (for some strange reason), you can lock the package version in Synaptic Package Manager. **Package** > **Lock Version**

---

### Post by easyease on 2006-08-02
sometimes its best to wait a few days before installing a new kernal, have a look on here and see if and what effect it has on other peoples machines.
 i know Nvidia card drivers and kernal upgrades can be a dicey combination.

---

### Post by Sweet Spot on 2006-08-02
Noted. Thank you both.

Edit: I uninstalled one of the components (network file sharing) but I couldn't find the other one listed to uninstall, which is Totem.

---

### Post by popkid on 2006-08-02
For some reason all the updates from today are listed as "local or obsolete" in synaptic... why is this? (they are also missing the little ubuntu logo next to them) its really basic stuff like gdm and gnome stuff...

pK

---

### Post by popkid on 2006-08-02
hmmm, seems that the reason is that the versions of all the packages I downloaded about an hour ago are no longer in the repositories...

they are all 2.4.10-0ubuntu1

whereas latest in repos are 2.4.6-0ubuntu2

will I have ended up with lots of corruptions?

pK

---

### Post by givré on 2006-08-02
let see your source.list, i suspect that some channel are disable, that's why you see the latest as 2.4.6 even if the latest **is** 2.4.10.

---

### Post by popkid on 2006-08-02
Hi... no... its the other way round, the packages I have are NEWER than those in the dapper sources

These is the case for every package installed by the auto update today

See attached screenshot...

pK

---

### Post by givré on 2006-08-02
It's simply because you disable the dapper-update channel after the upgrade. 
The latest gdm from dapper-upadete is as i said, 2.4.10.

---

### Post by popkid on 2006-08-02
I've not disabled anything, all sources check boxes are checked...

edit: added screenshot of source list

And it definitely says the latest dapper version is 2.14.6, its shown in the original screenshot!

the 2.14.10 versions were only downloaded about 2 hours ago now, i can't see any reference anywhere to 2.16.x versions...

Sorry, really confused by this now

pK

---

### Post by givré on 2006-08-02
Let see your /etc/apt/source.list.
A little explanation:
There is currantly 4 channel in dapper
- dapper is the channel of the release. The version are the same as from the CD. It don't change after the release.
- dapper-security provide security update
- dapper-update provide update of package
In each channel, there is 4 category:
- main, restricted, universe and multiverse.
You have to be sure that dapper-update main restricted is avaible for binary and nor only for source.
If you post here your /etc/apt/source.list i could point you the possible problem

---

### Post by popkid on 2006-08-02
ok, got it to move the packages into installed list by manually adding a binary reference for updates in addition to the source reference, it still gives latest version as 2.4.10 though... not 2.6.x

pK

---

### Post by popkid on 2006-08-02
sources list now looks like this...

```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
```

Thankyou for your help,

what would have caused a binary source to be lost from the repositories list?

pK

---

### Post by givré on 2006-08-02
ok, the 2.6.10 was a stupid typo (just change it). Anyway, i think you find the problem.

---

### Post by givré on 2006-08-02
> **popkid said:**
> 
what would have caused a binary source to be lost from the repositories list?

pK
no idea, that's quite strange.
Did you install any third party programm that could change your source.list (automatix...) after the upgrade?

---

### Post by popkid on 2006-08-02
I have had easyubuntu on there before, but haven't used it recently.

Anyway as you said, problem seems to be fixed!

Thankyou again,

pK

---

