---
title: "Just Installed Setting Up"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by Richman on 2005-08-02
I have installed ubuntu but iam trying to do this [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

when i try to do what it says in the guide i only get a file with the below in and the guide has lots more i dont know what has happened their. I understand i need to do this before i can do any other installing. 

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

Richard

---

### Post by the_purulent on 2005-08-02
You'll notice in the guide their are two seperate files. One as the default, and one that you should replace your default with. Make your file look like this:
> 
## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by poofyhairguy on 2005-08-02
[QUOTE=Richman]I have installed ubuntu but iam trying to do this [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

when i try to do what it says in the guide i only get a file with the below in and the guide has lots more i dont know what has happened their. I understand i need to do this before i can do any other installing. 



Richard[/QUOTE]


Delete whats in that file. Paste in what the other poster gives you.

---

### Post by Richman on 2005-08-03
Thanks for your help with that i think that is now working but now i have a new problem. 

When i try to install a package using the commang given it keeps giving me errors, see sample below..
> 
richman@equinox:~$ sudo apt-get install easytag
Reading package lists... Done
Building dependency tree... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  language-support-en: Depends: mozilla-firefox-locale-en-gb but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
 maybe something is missing that it wants.

In every file is says > Depends: mozilla-firefox-locale-en-gb but it is not going to be installed

Rich

---

### Post by poofyhairguy on 2005-08-03
[QUOTE=Richman]Thanks for your help with that i think that is now working but now i have a new problem. 

When i try to install a package using the commang given it keeps giving me errors, see sample below..
 maybe something is missing that it wants.

In every file is says 

Rich[/QUOTE]

put this in:

> sudo apt-get update

Close Firefox and try again.

---

### Post by Richman on 2005-08-03
Yea tried that, i get the same error over and over. Is thir anyways i can install what it wants manually?

Rich

---

### Post by poofyhairguy on 2005-08-03
[QUOTE=Richman]Yea tried that, i get the same error over and over. Is thir anyways i can install what it wants manually?

Rich[/QUOTE]

Sure. Download it here.

[http://packages.ubuntu.com/hoary/web/mozilla-firefox-locale-en-gb](http://packages.ubuntu.com/hoary/web/mozilla-firefox-locale-en-gb)

install with this way:

sudo dpkg -i nameofdeb.deb

---

### Post by Richman on 2005-08-03
\\:D/ Fixed my first problem

Richard

---

