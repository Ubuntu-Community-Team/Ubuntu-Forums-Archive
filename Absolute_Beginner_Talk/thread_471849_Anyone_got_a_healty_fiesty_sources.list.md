---
title: "Anyone got a healty fiesty sources.list"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-06-12
Mine has gone wierd it generates loads of errors when i update sources. When i try reload in the gnome version it gets to downloading 69/80 then just stops dead.

---

### Post by Seisen on 2007-06-12
Post your source list and we can fix for you, possibly.

---

### Post by starcraft.man on 2007-06-12
> **dgrafix said:**
> Mine has gone wierd it generates loads of errors when i update sources. When i try reload in the gnome version it gets to downloading 69/80 then just stops dead.

[Here is a good sources list.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

Some errors aren't actually the list though, if you want to know for sure just paste the errors you get in the terminal to here. As well as your sources list and well try and fix it up right.

---

### Post by muximus on 2007-06-12
what do you mean by in the gnome version??.... and well you could make a basic sources.list with only the official ubuntu repos, but you would lose all the sources that you added ob your own..

---

### Post by bapoumba on 2007-06-12
In addition, please paste the complete output to:
```
sudo aptitude update
```

---

### Post by Motoxrdude on 2007-06-12
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://ubuntu.beryl-project.org/ feisty main
```

I have some extra repositories on the end for beryl so you can take that out if you want. Hope this helps.

---

### Post by dgrafix on 2007-06-12
Thanks all :) its working again

lol by gnome version i meant the system>admin>software sources (didnt knw what else to call it :/ )

---

### Post by starcraft.man on 2007-06-12
> **dgrafix said:**
> Thanks all :)

lol by gnome version i meant the system>admin>software sources (didnt knw what else to call it :/ )

Ah, ok. Well just in case you need to edit it more manually later you can edit it with a text editor (its just a text file, most people do it this way).

```
gksudo gedit /etc/apt/sources.list
```

or if you got no GUI for whatever reason...

```
sudo nano /etc/apt/sources.list
```

## Number signs in front of text means it won't be read by apt and any other program that uses it, usually its a description. The rest are just links to the repos of course. 

Anyway, just a little pointer for future. Glad ya got it fixed.

---

