---
title: "repository mucked up"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by joep on 2007-01-30
Getting this error message.

E: Type ‘wget’ is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.

---

### Post by taurus on 2007-01-30
There is something wrong with the first line in your /etc/apt/sources.list.  Can you post it here?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by jvc26 on 2007-01-30
Can you post up the contents of your sources.list please
Il

---

### Post by joep on 2007-01-30
wget -O- --quiet [http://nvidia.limitless.lupine.me.uk/ubuntu/root@lupine.me.uk.gpg](http://nvidia.limitless.lupine.me.uk/ubuntu/root@lupine.me.uk.gpg) | sudo apt-key add 

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe main multiverse restricted
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

---

### Post by taurus on 2007-01-30
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the first line in there.

```
wget -O- --quiet http://nvidia.limitless.lupine.me.uk...pine.me.uk.gpg | sudo apt-key add 
```

I believe you need to run that line from a terminal, not adding it to your /etc/apt/sources.list.

---

### Post by jvc26 on 2007-01-30
> **taurus said:**
> 
```
wget -O- --quiet http://nvidia.limitless.lupine.me.uk...pine.me.uk.gpg | sudo apt-key add 
```

I believe you need to run that line from a terminal, not adding it to your /etc/apt/sources.list.
Yup, thats correct. Then, after removing the line and saving, run the wget command in terminal and then:
```

sudo apt-get update

```
Il

---

### Post by joep on 2007-01-30
Thank you for your help problem fixed. :D  Will I ever get the hang of this :)

---

### Post by jvc26 on 2007-01-30
You certainly will, just give it time and lots of use :)
Il

---

### Post by joep on 2007-01-30
Thanks once again if it wasn't for this forum I would be forced back to Windows. But the truth is I'm enjoying Ubuntu to much. :KS

---

