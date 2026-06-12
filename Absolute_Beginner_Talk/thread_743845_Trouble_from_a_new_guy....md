---
title: "Trouble from a new guy..."
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by morellib on 2008-04-03
Alright, I've been using Gutsy for probably close to six months now and I've loved every second of it. (Scrapped XP cause of the absurd amount of errors and trouble I was having). 

Everything (except for getting my memory card reader to read Magic Gate Memory Sticks on my dell) I've tried has worked perfectly. I recently decided to give K9Copy a try. I had read that I needed download some restricted formats and things of the like so my dvd drive would be able to read encrypted DVD's. 

Every time I try to add the formats, or really at this point do anything I get this message: 

```
E: Malformed line 79 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
```

I'm not sure what to do and there seems to be next to nothing listed about this problem on the whole of the internets... 

Any help would be greatly appreciated (and if anyone has any idea of how to get my memory card reader to check out my mem sticks that'd be cool too, but I've a feeling that's something I'll just have to live without). 

Thanks!

---

### Post by kesman on 2008-04-03
Could you paste the output of command:
```

cat /etc/apt/sources.list

```
so we could see what's wrong in there.

---

### Post by tubasoldier on 2008-04-03
Did you add a software repository to get the needed software?

---

### Post by morellib on 2008-04-03
Kesman- Here's the result: 

```
morellib@morellib-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb http://packages.medibuntu.org/ gutsy free non-free
deb deb-src http://packages.medibuntu.org/ gutsy free non-free
```



and Tubasoldier, I'm really sorry, but I have absolutely no idea what you just asked me haha

---

### Post by girishv on 2008-04-03
**deb deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free**

The problem is in the last line of your file. Either comment it out or remove one of
deb or deb-src from the line.
I suggest you to comment out it and run
sudo apt-get update


Girish

---

### Post by rockstar82 on 2008-04-03
You could also comment out the very first line, so that apt-get don´t stop when it can't find the cdrom.

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```

If i where you, i would make a backup of the current sources.list, and then manually try to restore the original look.

---

### Post by morellib on 2008-04-03
So I tried to comment out line number 79 as you suggested Girish, but my sources.list seems to be blank now... 

With this new development I attempted to install k9copy, but I thought I'd try to go through synaptic rather than muddle through code again (clearly I'm not very good at that part yet...)

k9copy is nowhere to be found in synaptic, so I attempted to muddle my way through the code after all. Of course this didn't work, everything seemed to be going along just fine and then mid-install this happened:

```
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

So once again I'm stuck, and my sources.list has vanished thereby preventing me from fixing anything you guys told me about... 

Sorry if I've buggered this up completely haha

---

### Post by Endwin on 2008-04-03
My mistake you moved them down to the bottom.

Not exactly sure why you would not have them in assides from not having the correct stuff for which list you want.

If you want an example here is one I use. 


```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

##Universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## Multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Backports

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by philinux on 2008-04-03
I think you'll find if you run

gksudo gedit /etc/apt/sources.list

copy and paste that.

Your sources list will be there for you to amend the last line.

---

### Post by morellib on 2008-04-03
Endwin- Not really sure what you meant (sorry for being ridiculous...) 

Philinux- when I put that line in the terminal I still get a blank page...

---

