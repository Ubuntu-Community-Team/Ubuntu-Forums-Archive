---
title: "Upgraded to Gutsy and notice &quot;install to hard drive&quot; option AFTER the upgrade"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by VitaminBB on 2007-11-11
So I finally got an upgrade to gutsy to work and when looking around I noticed a few things 

**1. **Under "System" there is an option called "Install" which says it will install "this system permanently to your hard drive".  

What does this mean exactly?

Is my upgrade just a temp thing?  My Feisty install was really installed, so what does this mean?


**2.** How do I get the dvd drive and hard drive icons back onto my desktop? They seemed to have disappeared when I upgraded (Still under "Places" just not on my desktop).


**3.** Under "Applications" there is a "Debian" area now full of links to programs etc, I never had the Debian area under Applications before, how do I just remove this from my Applications menu?

Also I removed checkgmail from my computer but the icon for it is still under Applications, how do I remove the icon?

---

### Post by bapoumba on 2007-11-11
> **VitaminBB said:**
> 
**1. **Under "System" there is an option called "Install" which says it will install "this system permanently to your hard drive".  

What does this mean exactly?

Is my upgrade just a temp thing?  My Feisty install was really installed, so what does this mean?

How did you install? An upgrade?
Could you please provide a screenshot (I'm not with Gnome and do not have this menu)?

> **VitaminBB said:**
> 
**2.** How do I get the dvd drive and hard drive icons back onto my desktop? They seemed to have disappeared when I upgraded (Still under "Places" just not on my desktop).
Please run in a terminal:
```
gconf-editor
```
Apps>Nautilus>Desktop>Tick the icons you want to see on the desktop.

> **VitaminBB said:**
> 
**3.** Under "Applications" there is a "Debian" area now full of links to programs etc, I never had the Debian area under Applications before, how do I just remove this from my Applications menu?

Do you have a Menu Editor?

---

### Post by matthewcraig on 2007-11-11
3. Use the Main Menu tool under your Preferences menu.

---

### Post by VitaminBB on 2007-11-11
Thanks Bapoumba, here is a snapshot of the image ...

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/scrnshot.jpg[/IMG]

---

### Post by bapoumba on 2007-11-11
Please post the output to:
```
cat /etc/apt/sources.list
sudo aptitude update
```

---

### Post by VitaminBB on 2007-11-11
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

#AUTOMATIX REPOS START

# deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted #universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted #universe multiverse
#AUTOMATIX REPOS END

Thats the whole thing, I had to comment out the automatix entry just to get the upgrade to work ...

---

### Post by VitaminBB on 2007-11-11
> **matthewcraig said:**
> 3. Use the Main Menu tool under your Preferences menu.

Thanks :)

You got to love noob questions eh *L*

---

### Post by bapoumba on 2007-11-11
> **VitaminBB said:**
> Thats the whole thing, I had to comment out the automatix entry just to get the upgrade to work ...
Yes, because they pointed to feisty repos. Any particular error to:
```
sudo aptitude update
```
?

If not, you're up to date :)

---

