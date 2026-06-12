---
title: "Is 5.10 an upgrade?"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by jamesroe on 2005-10-25
I downloaded Breezy Badger 5.10 last night (now running Hoary Hedgehog 5.04) and I am wondering if 5.10 is an upgrade - ie, will installing it over my current system keep all my personal settings and some of the programs (eg , wine) that I have running.

Or would I be starting from scratch with a new installation?

Jim Roe

---

### Post by linbetwin on 2005-10-25
5.10 is not an upgrade. If you want to upgrade and keep your settings, open a terminal and type:
> sudo apt-get update
sudo apt-get upgrade

---

### Post by Mustard on 2005-10-25
5.10 is the latest version of Ubuntu.  I assume you have downloaded the latest ISO from your post above.  You could use that ISO to install 5.10 in a clean install OR if you wish to 'upgrade' your Hoary Hedgehog to Breezy Badger while keeping all your old settings, you will need to follow this guide here in the wiki.

[https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28breezy%29%7C%28upgrade%29](https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28breezy%29%7C%28upgrade%29)

---

### Post by Strangerdave on 2005-10-25
Don't you have to modify the repositories though, changing everything that says Hoary to Breezy?  I did that first, then did the apt-get update, apt-get upgrade and everything went as planned.  None of my settings was altered.

But then again you were asking if the CD was an upgrade.  I believe there is an option to upgrade with the CD, and it shouldn't change what you have.

I would do the online upgrade.  It may take a while, but it was easy ;) 

-Sd-

EDIT** Well looks like someone beat me to a reply.

---

### Post by manicka on 2005-10-25
There have been different opinions on update or clean install. If you only have the breezy cd and a slow connection I'd suggest a clean install. If you have a reasonable connection I'd give update a go. 

Change all the repos entries from hoary to breezy. If you not sure have a look at aysiu's examples at [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html) and go for it.

```
sudo apt-get update 
sudo apt-get dist-upgrade
```
 
You'll be asked some questions during the upgrade, just accept the defaults.

Having said all that I updated about a month out from release and crashed and burned because I answered one of the config questions incorrectly and the i686 kernel wasn't quite up to scratch at that stage. I could have persevered and fixed it, but I caved in and clean installed..... such a wimp

---

### Post by clearnitesky on 2005-10-25
If you've got your home folder on a separate partition then you can re-install the distro over the other partitions without losing your settings. You would, however, lose any extra programs and libraries that you've installed since you installed Hoary 5.04 ;)

---

