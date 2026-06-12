---
title: "Just Installed Ubuntu 7.04 and the updates fail"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by Farkel on 2008-04-21
I just installed Ubuntu 7.04 and when I go to the update manager and try to update all of the packages fail. I don't know what the problem is. Anyone have an idea what might be wrong?:confused:

---

### Post by wolfen69 on 2008-04-21
did you install ubuntu without an internet connection?

---

### Post by Oldsoldier2003 on 2008-04-21
Please run these commands in a terminal and paste the resulting error messages ;

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Farkel on 2008-04-21
I installed it while not connected to the internet, but I'm connected now.

When I put the code into the terminal it said

E: The update command takes no argument

---

### Post by skymera on 2008-04-21
Isnt 7.04 unsupported now?

Since 8.04 is out in 2/3 days.

---

### Post by lswest on 2008-04-21
you have to do one line per command so ```
sudo apt-get update
``` and then```
sudo apt-get upgrade
```

---

### Post by Farkel on 2008-04-21
One of my friends just came in and told me that my Network Admin hasn't unblocked the site so I can't connect right now, but I am going to go talk to him and try to get it unblocked.

---

### Post by Oldsoldier2003 on 2008-04-21
> **skymera said:**
> Isnt 7.04 unsupported now?

Since 8.04 is out in 2/3 days.

7.04 is supported until oct 2008 (the releases have a 18month support cycle, LTS releases have 3/5years for desk/server IIRC)

---

### Post by Michael.Godawski on 2008-04-21
Coming back to the failed update.. Can you please post the output of this terminal command:
```

cat /etc/apt/sources.list
```

It will show us if everything is fine with your sources.

---

### Post by Farkel on 2008-04-21
This is what the last code came up with


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

---

