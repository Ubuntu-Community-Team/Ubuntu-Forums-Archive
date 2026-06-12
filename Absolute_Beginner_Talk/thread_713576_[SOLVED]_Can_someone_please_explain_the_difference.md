---
title: "[SOLVED] Can someone please explain the difference?"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-03-02
What are the differences between ubuntu, xubuntu, kubuntu, mythbuntu, feisty fawn, and any other ubuntu's that are out there. please go into detail and tell me the pro's and con's of each. i'm using ubuntu gusty gibbon right now and i like it but i'm wanting to see if there might be one better for me out there.

-thank you

---

### Post by JoshuaRL on 2008-03-02
Every version of Ubuntu has the same base OS.  The difference for the different versions is the Desktop Environment (DE).  Default Ubuntu uses [Gnome.](http://en.wikipedia.org/wiki/GNOME)  It is usually a little easier to use, and doesn't overwhelm the new user with a ton of configuration stuff.  It's aim is simplicity.

Kubuntu uses [KDE.](http://en.wikipedia.org/wiki/KDE)  It is based on ultimate configurability, and some feel that its menu layout and overall feel is more like Windows than Gnome.  It can be a little bit of graphics hog though.  A lot of longer-time users like KDE for the ability to configure it how they want, plus its a little more powerful.

Xubuntu uses [XFCE.](http://en.wikipedia.org/wiki/XFCE)  It is the more lightweight one of the three, using much less sytem resources and usually booting up faster.  It is good all-around, but tends to work really well on older computers or laptops.

---

### Post by decoherence on 2008-03-02
the animal code names refer to versions. gutsy gibbon is the latest release.

kubuntu, xubuntu etc are variants of ubuntu that replace the default user interface of the system. mythbuntu is a varient devoted to mythtv.

in general you should be using ubuntu unless you have reason to do otherwise. try kubuntu if you're feeling adventurous. try xubuntu if you have older hardware.

---

### Post by steveneddy on 2008-03-02
[Look here.]("http://www.ubuntu.com/")

---

### Post by SOULRiDER on 2008-03-02
Feisty Fawn, Gutsy Gibbon, Dapper Drake are all versions of Ubuntu, pretty much like what XP and Vista are, just only six months appart and not over a decade,

The main difference between *buntu is the default package sinstalled especially (what you will immediately notice) the desktop enviroment. Its basically a different set of default apps and a different GUI with their pros and cons..

---

### Post by Rocket2DMn on 2008-03-02
When you hear terms like Dapper Drake, Edgy Eft, Feisty Fawn, Gutsy Gibbon, and Hardy Heron - these are versions of Ubuntu that have been / will be released.  Ubuntu releases on a 6 month cycle with Dapper Drake being an LTS release (long term support - 3 years for desktop, 5 years for servers).  Gutsy Gibbon is the latest stable release, and Hardy Heron is due in April and it will be the next LTS release.  
Each has a number associated with it - the year it was released, and the month.
6.06 = Dapper - June, 2006
7.10 = Gutsy - October, 2007
8.04 = Hardy - April, 2008.

---

### Post by Tatty on 2008-03-02
Ubuntu is the main (standard) release.  Each version of Ubuntu is given a name and a number.  Up to now we have had:

Ubuntu 4.10 - Warty Warthog
Ubuntu 5.04 - Hoary Hedgehog
Ubuntu 5.10 - Breezy Badger
Ubuntu 6.06 - Dapper Drake
Ubuntu 6.10 - Edgy Eft
Ubuntu 7.04 - Feisty Fawn
Ubuntu 7.10 - Gutsy Gibbon

The numbers are based upon the date that each version is released.  so 6.10 is October of 2006, 7.10 is October of 2007, 7.04 is April of 2007.

Kubuntu is basically Ubuntu but with the KDE Desktop Environment pre-installed instead of Gnome (which is the default Desktop Environment in Ubuntu).  Xubuntu is the same, but with the XFCE Desktop Environment installed.

Which ever distro you choose, it doesnt matter as you can install any desktop environment you want, you can have all of them installed if you wish and choose which one you want to log into each time.  The only reason that Kubuntu and Xubuntu exist is simply to make life a bit simpler, so it is all set up for you with the particular Desktop Environment you want.

Mythbuntu again is basically just ubuntu Ubuntu, but it is optimised for ease of use of MythTV... Again you can install all the "bits" of mythbuntu on any ubuntu system.  Its just there for simplicity and ease of use.

---

### Post by JoshuaRL on 2008-03-02
And if you are sure you want to try another DE, but don't want to reinstall the OS, you can use aptitude:
```

sudo aptitude install kubuntu-desktop

```
That also works for **xubuntu-desktop** and **mythbuntu-desktop**. (forgot that one in the earlier post).  If you ever want to uninstall them, use aptitude too:
```

sudo aptitude remove kubuntu-desktop

```

To try out another DE after install, go to the Sessions button when logging in and chose the DE of your choice.

---

### Post by Rocket2DMn on 2008-03-02
Josh is correct, esp. about using aptitude.  Aptitude keeps track of the packages installed so it's easy to remove the *buntu-* metapackages and everything they came with with the simple remove command.  If you used apt-get instead, you would have to manually remove most of the packages that *buntu-* links to ( which can be done, it's just a little more trouble: see here - [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) )

---

### Post by RadiationHazard on 2008-03-02
alright thanks for the reply's guys. they've really helped me alot. I think i'm going to try out kubuntu. I'm really good at making my appearances look good with ubuntu but i want to try something harder. =]

---

### Post by SOULRiDER on 2008-03-02
IMHO a fresh install is ALWAYS WAY BETTER than installing the *buntu-desktop packages, but thats your decision.

---

### Post by JoshuaRL on 2008-03-02
> **RadiationHazard said:**
> alright thanks for the reply's guys. they've really helped me alot. I think i'm going to try out kubuntu. I'm really good at making my appearances look good with ubuntu but i want to try something harder. =]

I'm doing the same thing right now.  I got Gnome looking how I wanted it, and wanted to configure something else.  After a bit I'll probably go to XFCE too.

By the way, Mythbuntu is XFCE based.

---

