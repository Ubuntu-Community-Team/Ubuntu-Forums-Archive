---
title: "Dependency not satisfiable"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by djen9999 on 2007-04-20
KMymoney was removed when I updated to Feisty.  My files were still intact so I figured it would be a simple process to reinstall KMymoney but I get the following error:  Dependency not satisfiable:KDElib4.

I don't normally use KDE but I have it installed since I use some KDE apps.

I checked Synaptic and I don't see a specific library 4 for KDE.  Can someone point me in the right direction?

---

### Post by Seisen on 2007-04-20
Try installing kdelibs through synaptic and see if that works.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=KDElibs&sourceid=mozilla-search]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=KDElibs&sourceid=mozilla-search")

---

### Post by djen9999 on 2007-04-20
It says that it's already installed.  In the mean time I attempted to install Audacity and I get a similar error libjack0.100.0-0.

What the hey?

---

### Post by Bachstelze on 2007-04-20
When asking for help, please paste the exact error messages you get.

---

### Post by djen9999 on 2007-04-20
I would love to but it wont copy.

---

### Post by Seisen on 2007-04-20
Post your source list I want to see something

---

### Post by djen9999 on 2007-04-20
My Synaptic Source list?

---

### Post by Seisen on 2007-04-20
Put this in the terminal 

```
sudo gedit /etc/apt/sources.list
```

---

### Post by djen9999 on 2007-04-20
AWWW.  Got it.  I think I'm on to the problem.  I'll print the source list to see if we're thinking along parallel lines.

---

### Post by djen9999 on 2007-04-20
Here it is and I see what's not ticked.  Ask enough questions and this dim bulb will finally light.  I think I can solve this on my own now.  Stay tuned in case I run in to more problems.  :) 

Thanks.

---

### Post by djen9999 on 2007-04-20
> **Seisen said:**
> Put this in the terminal 

```
sudo gedit /etc/apt/sources.list
```

Coming from a windows background, I always take the long way around.  I keep forgetting about the terminal how incredibly useful it is.  

Thanks again

---

### Post by Seisen on 2007-04-20
It takes a little while to get used to the terminal.

---

### Post by djen9999 on 2007-04-20
Still having a few problems.  Here's the source list



deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by Seisen on 2007-04-20
Try using kdelibs5 from that link I gave you and see if that works.

---

### Post by djen9999 on 2007-04-20
KEDlibs5 said that it was already loaded, however when I tried to download KMymoney again, it loaded fine.  No error messages or problems.

---

