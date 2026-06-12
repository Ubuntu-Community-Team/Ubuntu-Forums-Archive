---
title: "stupid Newbie thing"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by maccawolf on 2007-03-30
when I got up for work this morning (20/20 hindsight..... 5:30 is too early to be playing with installing stuff) I tried to install Wine in my box.

Anyway, I used sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list

to try to d/l & install Wine.  Problem is, that now when I'm more fully awake, I realize I missed the previous step, which apparently has rendered my computer FUBAR. How do I remove that stuff of find it to try to fix it?

Can't open SYNAPTIC or ADD/REMOVE cos of it. When I try , I get an error something like nothing exists, or something like that.:confused: :confused:

---

### Post by gjtoth on 2007-03-30
> **maccawolf said:**
> when I got up for work this morning (20/20 hindsight..... 5:30 is too early to be playing with installing stuff) I tried to install Wine in my box.

Anyway, I used sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list

to try to d/l & install Wine.  Problem is, that now when I'm more fully awake, I realize I missed the previous step, which apparently has rendered my computer FUBAR. How do I remove that stuff of find it to try to fix it?

Can't open SYNAPTIC or ADD/REMOVE cos of it. When I try , I get an error something like nothing exists, or something like that.:confused: :confused:

Try "sudo apt-get remove wine" in a console

---

### Post by maccawolf on 2007-03-30
THANKS! will try that when I get home from work.

---

### Post by zvacet on 2007-03-30
Why don´t you install it from synaptic or add/remove?

---

### Post by maccawolf on 2007-03-30
WHY? cos it's already broken, if you mean why DIDN'T I, it's prolly cos when I searched for it in add/remove, I couldn't find it, and same in synaptic.:lolflag:

---

### Post by maccawolf on 2007-03-30
Tried it. The NEW error I get is this:
E: type "--06:44:03--" is not known on line l in source list /etc/apt/sources.list.d/winehq.list

E: the list of sources could not be read.

Did cat /etc/apt/sources.list and got THIS:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://getautomatix.com/apt](http://getautomatix.com/apt) edgy main
lobo@lobo:~$

---

### Post by zvacet on 2007-03-31
Go to the update manager to be sure you have all repositories open(chek all boxes).Close and reload.Lines in source list should look like this:
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

and not

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

Try remove it with 

```
sudo apt-get remove --purge 
```

When you are done with all of this you should be able to see wine in synaptic.

---

### Post by mr_ed on 2007-03-31
I just found out today that the wine repo isn't stored in /etc/apt/sources.list.

Type 
cat /etc/apt/sources.list.d/winehq.list
and you should see the --06:44:03-- at the top of that file.

---

### Post by zvacet on 2007-03-31
[http://sourceforge.net/project/showfiles.php?group_id=6241]("http://sourceforge.net/project/showfiles.php?group_id=6241")

Download Ubuntu deb file

---

### Post by maccawolf on 2007-04-01
Only 86,000 to chose from....LOL

Which one do I download?

---

### Post by jvc26 on 2007-04-01
If you look at your /etc/apt/sources.list file there will be, at line 1 the entry --06:44:03--. This is why youre getting that error. You need to delete that, save the file and sudo apt-get update and that should fix the issue with the sources.list then you can add the wine repo:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
gksudo gedit /etc/apt/sources.list

```
Add this line to the bottom:
```

http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list

```
Then
```

sudo apt-get update
sudo apt-get install wine

```
Il

---

### Post by maccawolf on 2007-04-01
Thanks! Tried that. I'll post the outcome later

---

