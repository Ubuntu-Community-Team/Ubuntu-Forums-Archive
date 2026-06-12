---
title: "apt-get autoremove Problems"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-11-27
I installed xubuntu-desktop yesterday for a particular reason. All I did was:

> sudo apt-get install xubuntu-desktop

Today, I went to uninstall it. I logged into my Gnome session, and did:

> sudo apt-get remove --purge xubuntu-desktop && sudo apt-get autoremove

It removed xubuntu-desktop just fine, but didn't remove any of the xubuntu dependencies. Am I going to have to figure out which ones are xfce-dependent and manually remove all of them? :'(

---

### Post by teryowen on 2007-11-27
actually i dont think so.

Just run the command autoremove seperatly i did it earlier today, because in the past it told me there is some things you no longer need.

I ran "sudo apt-get autoremove" and it showed me what it was going to remove and i just agreed by doing the "Y" key thinkg, and worked, so just try it on its own.

---

### Post by meborc on 2007-11-27
when installing metapackages depending on a LOT of different packs, aptitude is much better to use as it "remembers" what was installed and removes all the programs afterwards... that said, i prefer apt-get to aptitude any day... :) </totally unhelpful text>

ok, i guess what you need to do is to find out what packages are the dependencies for xubuntu-desktop and remove them all... i don't know if there is any better way of doing this

the packages should be listed here : [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by FuturePilot on 2007-11-27
See here for how to completely remove Xubuntu
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")
For future reference, when you install entire desktop environments it's better to use aptitude instead, since you can easily remove everything with aptitude remove

---

### Post by tonyr1988 on 2007-11-27
> **teryowen said:**
> actually i dont think so.

Just run the command autoremove seperatly i did it earlier today, because in the past it told me there is some things you no longer need.

I ran "sudo apt-get autoremove" and it showed me what it was going to remove and i just agreed by doing the "Y" key thinkg, and worked, so just try it on its own.

> tony@tony-laptop:~$ sudo apt-get autoremove 
[sudo] password for tony:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

> **meborc said:**
> when installing metapackages depending on a LOT of different packs, aptitude is much better to use as it "remembers" what was installed and removes all the programs afterwards... that said, i prefer apt-get to aptitude any day... :) </totally unhelpful text>

ok, i guess what you need to do is to find out what packages are the dependencies for xubuntu-desktop and remove them all... i don't know if there is any better way of doing this

the packages should be listed here : [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

I used to use aptitude, but since apt-get implemented the autoremove function, there wasn't really a reason for me to keep using aptitude (since apt-get autoremove has always worked for me before). :(

---

### Post by meborc on 2007-11-27
you posted the same time as FuturePilot... i hope you don't miss his post ;)

---

### Post by tonyr1988 on 2007-11-27
> **FuturePilot said:**
> See here for how to completely remove Xubuntu
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")
For future reference, when you install entire desktop environments it's better to use aptitude instead, since you can easily remove everything with aptitude remove
Thanks a lot. It wanted to remove a few other applications that I wanted (like amarok and k3b), but those were easy re-installed.

---

