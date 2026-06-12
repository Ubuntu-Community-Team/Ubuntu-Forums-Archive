---
title: "segmentation fault (core dumped)"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Hope on 2007-05-25
Hello, hello, hello. Whats this then?

I got this message > segmentation fault (core dumped)
after entering a command in the terminal eg. > sudo aptitude install build-essential
sounds serious, any ideas what this is, what I've done, and more importantly, to me, is how do I fix it?
I've been trying pretty hard to get my printer to work and perhaps some reckless installing got this?

Any and all advice is appreciated.
Thanks.

---

### Post by taurus on 2007-05-25
Do you still get the same error message if you run

```
sudo aptitude update
sudo aptitude install build-essential
```
Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by init1 on 2007-05-25
"segmentation fault" usually means that the executable that you are trying to run cannot be run. I am not sure what the "(Core dumped)" means

---

### Post by Hope on 2007-05-25
Hi Taurus, yeah still the same error.
here's the /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

Hey, and thanks for the speedy response guys.

---

### Post by taurus on 2007-05-25
Did you receive the same error message before or after you installed Automatix?

---

### Post by Hope on 2007-05-25
Well, I guess it must be after, but not immediately after.
So I assume I should uninstall Automatix? I've got the apps I wanted so its no trouble, or will uninstalling cause a  problem with those?

---

### Post by taurus on 2007-05-25
I am not sure why you feel like you need to install Automatix with Feisty because everything that you need is available from Add/Remove, synaptic, apt-get, or aptitude.

You can try and remove Automatix

```
sudo aptitude --purge remove automatix2
```
then edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove all the lines related to Automatix.  Then, save the changes and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by arnieboy on 2007-05-25
aptitude/apt segfaulting has **nothing to do with Automatix**....
It is happening because the OP's apt cache has got corrupted.
The issue can be resolved by doing
```
sudo rm -f /var/cache/apt/*.bin
sudo apt-get update
```

-Arnie
Automatix Team Lead

---

### Post by confused57 on 2007-05-25
> **arnieboy said:**
> aptitude/apt segfaulting has **nothing to do with Automatix**....
It is happening because the OP's apt cache has got corrupted.
The issue can be resolved by doing
```
sudo rm -f /var/cache/apt/*.bin
sudo apt-get update
```

-Arnie
Automatix Team Lead

Welcome back arnieboy, Automatix has never let me down, I've used it in Breezy, Dapper, Edgy, Feisty, Mepis, Xubuntu, and Debian Etch...it's worked  flawlessly in all of them, except for user error when I installed the wrong version.

---

### Post by arnieboy on 2007-05-25
> **confused57 said:**
> Welcome back arnieboy, Automatix has never let me down, I've used it in Breezy, Dapper, Edgy, Feisty, Mepis, Xubuntu, and Debian Etch...it's worked  flawlessly in all of them, except for user error when I installed the wrong version.
Hey nice to be back and thanks :)

---

### Post by Hope on 2007-05-26
Ok, first off, I installed Automatix because it was recommended as simple to use, and it is. I didn't know about the alternatives.
Second, Arnieboy, I did that command and it ran without errors, but the original command still gives me the same error ie segmentation fault.
I think now I'll try Taurus' fix and let you know the result.

---

### Post by arnieboy on 2007-05-26
> **Hope said:**
> Second, Arnieboy, I did that command and it ran without errors, but the original command still gives me the same error ie segmentation fault.

Taurus's suggestion will not fix aptitude (it will simply remove automatix and its repository and some official Ubuntu repositories ).
Did you run the two commands one after the other (pressing enter after each step?)
Also, what does:
```
sudo apt-get install build-essential 
```
give? I want to know if both apt-get and aptitude are segfaulting. You need to remember that any package you try to install with aptitude will fail because of the corrupt cache.

---

### Post by Hope on 2007-05-26
OK, i just tried the command to purge automatix but I got the same error - segmentation error.
So i went into automatix and chose remove automatix repos which it did (I checked).
tried aptitude update but back to that error!
it seems to be something else?
Just saw your post Arnieboy, apt-get is working right now!
and I think I put in your commands wrong ie I copied and pasted the entire thing. Sorry.

---

### Post by gradedcheese on 2007-05-26
> **init1 said:**
> "segmentation fault" usually means that the executable that you are trying to run cannot be run. I am not sure what the "(Core dumped)" means

A segmentation fault is an invalid memory access by the program you were running (ie: it tried to access memory that it is not allowed to access, such as a kernel space address).  When this happens, a [core dump]("http://en.wikipedia.org/wiki/Core_dump") is generated for your convenience.  It's literally a dump (snapshot) of the program's state at the time of failure, it's made for developers to be able to track down what happened and fix it.

---

### Post by arnieboy on 2007-05-26
> **Hope said:**
> 
Just saw your post Arnieboy, apt-get is working right now!
and I think I put in your commands wrong ie I copied and pasted the entire thing. Sorry.
good.. 
now do the following:
```
sudo apt-get --purge remove aptitude
sudo apt-get install aptitude
```
and then use aptitude to install any package just to test or just do:
```
sudo aptitude update
```
I don't know if purging aptitude will reset its cache but let's see.

---

### Post by Hope on 2007-05-26
Arnieboy, that fixed it!
Thank you very much.:D
now I've run the other commands and it has also finished properly so now I can test the printer
to everyone who has answered my posts a sincere thanks.:D

---

### Post by leetcharmer on 2007-07-15
I did everything listed by arnieboy, but that doesn't help.  Everytime I install an application, it states "segmentation fault (core dumped)" before all the other text in the terminal.  Then it proceeds to install everything just fine, but why is segmentation fault (core dumped) there?

---

