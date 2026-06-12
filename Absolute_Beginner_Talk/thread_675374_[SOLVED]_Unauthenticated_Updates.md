---
title: "[SOLVED] Unauthenticated Updates????"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by tahitiwibble on 2008-01-22
It seems like 7 out of 10 times I automatically update 7.04 on my machine I get "Warning! You are about to install software that cannot be authenticated. Doing this could allow a malicious individual to take control of your system."

Am I living in Ubuntu Fools Paradise because up until now I have always ignored the message. Now I'm worried.

---

### Post by bodhi.zazen on 2008-01-22
You are probably "OK"

post your /etc/apt/sources.list if you want us to look it over.

---

### Post by Paul820 on 2008-01-22
I get that all the time, my sources are all trusted. As long as you only use trusted sources you will be fine as **bodhi.zazen** said.

---

### Post by tahitiwibble on 2008-01-22
dad@dad-desktop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
dad@dad-desktop:~$ 


Oh o?????

---

### Post by mister_pink on 2008-01-22
sources.list is just a text file, you need to use something to display it:
cat /etc/apt/sources.list

---

### Post by Paul820 on 2008-01-22
You can copy and paste it from the terminal by typing
> sudo cat /etc/apt/sources.list
or type
> gksudo gedit /etc/apt/sources.list
and copy and paste it from there. It's up to you which one you do.

---

### Post by Dual Cortex on 2008-01-22
You're simply typing the location of the file to the terminal.
Either type 
```
cat /etc/apt/sources.list
```
or 
```
gedit /etc/apt/sources.list
``` 
to see the contents of the file.

---

### Post by tahitiwibble on 2008-01-22
Wow .........

dad@dad-desktop:~$ sudo cat /etc/apt/sources.list
Password:
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://pf.archive.ubuntu.com/ubuntu/](http://pf.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://pf.archive.ubuntu.com/ubuntu/](http://pf.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pf.archive.ubuntu.com/ubuntu/](http://pf.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://pf.archive.ubuntu.com/ubuntu/](http://pf.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://pf.archive.ubuntu.com/ubuntu/](http://pf.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://pf.archive.ubuntu.com/ubuntu/](http://pf.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pf.archive.ubuntu.com/ubuntu/](http://pf.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://pf.archive.ubuntu.com/ubuntu/](http://pf.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pf.archive.ubuntu.com/ubuntu/](http://pf.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://pf.archive.ubuntu.com/ubuntu/](http://pf.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
dad@dad-desktop:~$

---

### Post by Paul820 on 2008-01-22
They are all ubuntu.com so they are safe repo's. Don't worry about it, it will be ok as long as you only use trusted sources. There must be a bug somewhere or something else has gone wrong with a script, who knows. I have not had any problems.

---

### Post by tahitiwibble on 2008-01-22
Thank you to you Gentlemen.

I'll keep an eye out from now on and check that same file from time to time also.

Thanks again, I am grateful.

---

### Post by bodhi.zazen on 2008-01-22
You are fine. You can get rid of those errors by importing the Ubuntu apt keys, but it is not necessary.

---

