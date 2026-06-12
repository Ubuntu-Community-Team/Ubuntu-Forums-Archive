---
title: "Repositories problem"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by Spacedementia87 on 2007-09-28
Trying to add this repository to my synaptic:

deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

but when i click reload i get this error:

[http://gb.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

and then i can get modules from this repository.  Is this outdated and no longer used or something?

---

### Post by shearn89 on 2007-09-28
Have you got the gpg key?
It could be that the file you're trying to get is corrupted or something...

---

### Post by Spacedementia87 on 2007-09-28
i'm not sure what the GPG key is...

I get the error before trying to download a file

---

### Post by shearn89 on 2007-09-28
I'm not sure what the gpg key actually does - i think its some sort of security thing to allow you to download from the repo.

are you by any chance following [this tutorial?]("https://help.ubuntu.com/community/CompositeManager/CompizFusion")
If not, i suggest you try it.

---

### Post by Malibu Illusion on 2007-09-28
Please post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by Spacedementia87 on 2007-09-28
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

#AUTOMATIX REPOS END
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
# deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main

```

I was following [this tutorial]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty")

---

### Post by Malibu Illusion on 2007-09-28
Okay, try this:

```
sudo rm -rf /var/lib/apt/lists/partial/*
```

Then:

```
sudo apt-get update
```

Your sources.list looks fine at first glance.

---

### Post by Spacedementia87 on 2007-09-28
```
jajh2@jajh2:~$ sudo rm /var/lib/apt/lists/patrial/*
rm: cannot remove `/var/lib/apt/lists/patrial/*': No such file or directory
```

---

### Post by Malibu Illusion on 2007-09-28
"patrial" != "partial"

Spell it properly.  In fact, just copy the command straight from my post into the terminal.

---

### Post by Spacedementia87 on 2007-09-28
ahh sorry was being stupid!

---

### Post by Malibu Illusion on 2007-09-28
I recommend an extra degree of care when using the "rm" command; a typo in the wrong place could render a system useless.

Anyway, after doing that use:

```
sudo apt-get update
``` 

And tell me if that resolved the problem.

---

### Post by Spacedementia87 on 2007-09-28
ok now it stops giving the error when i reload the repositories but i still get this when i mark compiz for installation:

```
compiz:
 Depends: compiz-plugins but it is not going to be installed
 Depends: compiz-gnome but it is not going to be installed
```

---

### Post by shearn89 on 2007-09-28
that can be fixed by 
```
sudo apt-get install compiz compiz-plugins compiz-gnome
```
can't it? Malibu will know...

---

### Post by Malibu Illusion on 2007-09-28
I recommend trying:

```
sudo aptitude install compiz compizconfig-settings-manager sexy-python emerald emerald-themes
```

Assuming you want those as the tutorial suggests.  Aptitude will install the recommended dependencies by default.  You will need to close Synaptic Package Manager before entering this.

---

### Post by Spacedementia87 on 2007-09-28
ok that seems to have worked pretty well not.  Thank you :)

One question, i have ticked the desktop cube button, but how do i use it?

---

### Post by Malibu Illusion on 2007-09-28
Well, I'm far from a Compiz expert.  In fact, I've never used it.

You may wish to check [this page](http://forlong.blogage.de/) which seems to provide details on using various aspects, though.  Or you can wait until someone who knows a little more about Compiz drops by.

Glad we resolved the core APT issues and installation, though.  

Take care.

---

### Post by Spacedementia87 on 2007-09-28
Yah, thanks alot :)

Followed that tutorial still can get it to switch desktops for some reason

---

### Post by sailor2001 on 2007-09-28
tou should have a compiz manager (system/preferences) but if you don't, go back to synaptics and locate it there (compiz manager)....set it up any way you so desire.  By default I leave the rotation as ctrl/alt-left click

---

### Post by bruce89 on 2007-09-28
> **Spacedementia87 said:**
> ```

[...]

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

#AUTOMATIX REPOS END

[...]


```

That's probably not a good idea.

---

### Post by Spacedementia87 on 2007-09-28
I can't see where to change the shortcuts.  And i have found my problem is that i need to log out and log back in for every change i make to it.

I also have a problem with the update manager flashing at me with the compiz core update.  But when I tell it to do the update it doesn't do anything.  Anyway to set it to ignore the updates for this?

---

