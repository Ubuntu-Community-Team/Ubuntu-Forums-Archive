---
title: "Help me please."
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Phoenix27 on 2007-10-07
I am trying to download a debian file and for some reason I get this error.

E: Type '“deb' is not known on line 45 in source list /etc/apt/sources.list
E: The list of sources could not be read.


I can't double-click the file either, and this error happens in terminal.

How can I fix this?

---

### Post by Dr Small on 2007-10-07
Please post your sources.list file:
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by forestpixie on 2007-10-07
open the file for editing

```
gksudo gedit /etc/apt/sources
```

got to line 45 and where it starts '&#8220;deb' - change it to read deb

then save and do

```
sudo apt-get update
```

---

### Post by Phoenix27 on 2007-10-07
Here

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
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”

---

### Post by forestpixie on 2007-10-07
it's both the end lines

use the command to edit the file and remove the " from the beginning of each, save and do the update command as I showed

---

### Post by Dr Small on 2007-10-07
Replace the last two lines with this:
```
deb http://www.getautomatix.com/apt feisty main
deb http://www.getautomatix.com/apt feisty main
```

Then run:
```
sudo apt-get update
```
as forestpixie stated.

Dr Small

---

### Post by Phoenix27 on 2007-10-07
Thank you very much :D

---

### Post by Dr Small on 2007-10-07
Please remember to mark your thread as solved, so others will know to read your thread to solve their problems, if they have the same.

Thread Tools > Mark as Solved

---

