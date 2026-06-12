---
title: "i need pnet or whatever??"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by FordInFlames on 2005-12-13
i need pnet to install gettext so i can install glib so i can install gtk so i can install blahblah blahblahlbha  why do u need 400.000+++ programs or whatever just to instal something geez!!

ps. i need something called pnet idont know if its a program or whatever just pliz help im goin insane i spend 4 hours a day straight just downloading, typing in the terminal and stuff just to make some programs work!

---

### Post by FordInFlames on 2005-12-13
found pnet on debian thank you there is a god!

---

### Post by hod139 on 2005-12-13
pnet is available in ubuntu as well.  You have to add the universe repository is all.  

You can use synaptic to add the universe repository, or replace your /etc/apt/sources.list with the following lines:
```

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

```

Note: I would suggest _not_ mixing debian and ubuntu packages if you can avoid it.

---

### Post by FordInFlames on 2005-12-13
i need to know how i install the thing ive tryed sudo apt-get install pnet but that didnt work to well!

---

### Post by hod139 on 2005-12-13
After you enable the extra repositories as I have shown in my previous post, you can simply type:
```

sudo apt-get install pnet

```

---

### Post by FordInFlames on 2005-12-13
[QUOTE=hod139]After you enable the extra repositories as I have shown in my previous post, you can simply type:
```

sudo apt-get install pnet

```[/QUOTE]

this is what happened
 
E: Type 'restricted' is not known on line 2 in source list /etc/apt/sources.list
E: The list of sources could not be read.

---

### Post by hod139 on 2005-12-13
Sorry about that, a funny paste happened.  Line 2 was suppose to be part of line 1, and commented out.  I am editing that fix now.

Edit: I fixed the sources.list file in my previous post.  You should be all set now

---

