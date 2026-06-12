---
title: "Ways of upgrading from fiesty to gusty"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by startgame412 on 2007-10-15
Hi, is it possible to upgrade from fiesty to gusty using the gusty release cd when it is released in 3 days? If so, how is this done. I cannot find any info about upgading using a cd. I can upgrade using hte network but it is somwhat slow 768k connection. This is for my ps3 which btw I am happy to see that someone is working on bringing the latest version of ubuntu to the ps3 as i have seen it available for download in hte form of daily builds. Any info is greately appriciated. Thanks.

---

### Post by Hospadar on 2007-10-15
Well the easiest way I think would be to move your home directory to a second partition, and then reinstall linux, and then re-install whatever packages.  I think you could probably also use aptoncd but I don't know exactly how to go about that.

---

### Post by Frak on 2007-10-15
Burn the alternate CD to Disc and run
```
gksu "sh /cdrom/cdromupgrade"
```
In the terminal

---

### Post by startgame412 on 2007-10-15
Hi thanks for replying. So the regular live cd will not work for upgrading the system? If it does not work for upgrading the system I may do a clean install.Thanks.

---

### Post by Frak on 2007-10-15
> **startgame412 said:**
> Hi thanks for replying. So the regular live cd will not work for upgrading the system? If it does not work for upgrading the system I may do a clean install.Thanks.
No, the regular CD doesn't work.

---

### Post by startgame412 on 2007-10-15
Thanks for the info. So upgrading over the network is the best ay or should I just do a clean insteall when gusty is released? Thanks.

---

### Post by oodledoodle on 2007-10-16
i assume you're connected to the internet? if so, this may be some help...

[http://onlyubuntu.blogspot.com/2007/09/upgrade-ubuntu-704-feisty-fawn-to.html](http://onlyubuntu.blogspot.com/2007/09/upgrade-ubuntu-704-feisty-fawn-to.html)

it explains how to upgrade to gutsy from feisty without having to burn a new cd. its probably the easiest way if you ask me.

---

### Post by Frak on 2007-10-16
I would reccomend installing clean, but that's just what I do because I'm weird that way (and its less messy)

Also, I just learned I'm using the final version of Gutsy. :)

---

### Post by startgame412 on 2007-10-16
How did you get to use the final version of gusty. It is not even out yet.

---

### Post by Frak on 2007-10-16
> **startgame412 said:**
> How did you get to use the final version of gusty. It is not even out yet.
It exists, it's just not "official" yet. Freezing usually occurs 5 days before release.

---

### Post by dynamethod on 2007-10-16
erm i was under the impression that all you had to do was run the update manager when gutsy is officially available, and that would present a "upgrade distro" option, then upgrade to gutsy from there

---

### Post by FuturePilot on 2007-10-16
> **Frak said:**
> It exists, it's just not "official" yet. Freezing usually occurs 5 days before release.

Mmm. Lots of bug fixes installing now:lolflag:

---

### Post by startgame412 on 2007-10-16
What do you mean by freezing ocuring about 5 days before offical relese date? There were 93 updates total to install after I installed gusty on a virtual machine so yes there are a lot of upates. SO once gusty is released, ther will be no more updates for fiesty?

---

### Post by Frak on 2007-10-16
> **dynamethod said:**
> erm i was under the impression that all you had to do was run the update manager when gutsy is officially available, and that would present a "upgrade distro" option, then upgrade to gutsy from there
Correct, this is if you want to upgrade before.

---

### Post by FuturePilot on 2007-10-16
Freezing is referring to the fact that there will be no new versions of apps added to the repos. The updates will only be bug fixes and security updates. Yes there will still be updates for Feisty throughout it's 18 month support life.

---

### Post by Frak on 2007-10-16
> **startgame412 said:**
> What do you mean by freezing ocuring about 5 days before offical relese date? There were 93 updates total to install after I installed gusty on a virtual machine so yes there are a lot of upates. SO once gusty is released, ther will be no more updates for fiesty?
Means no more changes to the final ISO image or apps to the repo before backports.

---

### Post by Drakkor on 2007-10-16
[http://www.thelinuxstore.ca/static/ubuntu_7_10_upgrade.html](http://www.thelinuxstore.ca/static/ubuntu_7_10_upgrade.html)

---

### Post by startgame412 on 2007-10-16
Thanks everyone.

---

