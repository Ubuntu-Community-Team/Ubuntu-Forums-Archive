---
title: "little problem"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by death_god on 2007-07-17
well i was using automatix to install wine and some other apps when automatix showed me an error, now everytime i try to install something on synaptics i can't install anything, i have the same problem with automatix and terminal. this is the error, E:Type 'O::deb' is not known on line 48 in source list /etc/apt/sources.list, E:The list of sources could not be read.'. what can i do?

---

### Post by dpar on 2007-07-17
Post the terminal output of gedit /etc/apt/sources.list
That way we can see where the error is.

---

### Post by death_god on 2007-07-17
i get a permission denied

---

### Post by Celegorm on 2007-07-17
try > cat /etc/apt/sources.list
either that or type "sudo " in front of the other command. sudo runs a command with root priveleges.

---

### Post by death_god on 2007-07-17
ok thanks, this is what i get with that.
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#AUTOMATIX REPOS START

O::deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by forestpixie on 2007-07-17
edit the line near the end which starts O:: to say 

```
deb http://wine.lowvoice.nl/apt feisty main
```

you'll need to do 

```
gksudo gedit /etc/apt/sources.list
```

backup first
```

sudo cp /etc/apt/sources.list /etc/apt/sources.bak
```

EDIT -
then 

sudo apt-get update

to update it

---

### Post by dpar on 2007-07-17
Ok, automatix made a boo boo(what a suprize:rolleyes:).

That line 48 Shouldn't have that 0:: in front of it.
you will have to edit it so that it just reads 'deb blah blah blah......

Go to terminal and do a > gksudo gedit /etc/apt/sources.list
After it opens up, go to the offending line and edit out just the 0::
then save and exit
evrything should be ok now:)


Edit: Man, I got to learn to type faster.:(

---

### Post by death_god on 2007-07-17
hey thanks alot that fix the problem.

---

### Post by dpar on 2007-07-17
Your very welcome.

---

### Post by forestpixie on 2007-07-17
no problem - have a good day/night :D

---

