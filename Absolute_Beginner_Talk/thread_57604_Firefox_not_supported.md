---
title: "Firefox not supported?"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by homersbrain on 2005-08-17
I've been having a few problems with software authenicity. Synapic says that firefox (or its gnome support) is not supported software as no ubuntu logo is next to it. I find this surprising as it comes with ubuntu! Also, in software updates, a warning window opens when that starts:
'It is not possible to upgrade all packages' and lists a firefox and a few others. What is happening? I had recently updated from a scripting link to install several programs at a time. Can anyone explain?

---

### Post by Strongbad on 2005-08-18
You might have a problem with your repositorys, but rather than try to mess with all that, you can download the original mozilla package from mozilla.org. It is really easy to install, just download it and find the setup program. 

TTFN!
-Strongbad-

---

### Post by nocturn on 2005-08-18
[QUOTE=homersbrain]I've been having a few problems with software authenicity. Synapic says that firefox (or its gnome support) is not supported software as no ubuntu logo is next to it. I find this surprising as it comes with ubuntu! Also, in software updates, a warning window opens when that starts:
'It is not possible to upgrade all packages' and lists a firefox and a few others. What is happening? I had recently updated from a scripting link to install several programs at a time. Can anyone explain?[/QUOTE]

Which Ubuntu version are you using?
What scripting link did you follow?

Can you post your /etc/apt/sources file?

---

### Post by homersbrain on 2005-08-19
OK, here is the contents of my sources file:

------------------------------------------

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


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
 
## hoary multiverse [added with ubuntu-addons.bash_v060]
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
 
## hoary multiverse [added with ubuntu-addons.bash_v060]
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
 
## hoary universe [added with ubuntu-addons.bash_v060]
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary universe
 
## hoary universe [added with ubuntu-addons.bash_v060]
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary universe
 
## hoary-security [added with ubuntu-addons.bash_v060]
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 
## hoary-security [added with ubuntu-addons.bash_v060]
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 
## hoary-backports [added with ubuntu-addons.bash_v060]
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
 
## hoary-extras [added with ubuntu-addons.bash_v060]
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
 
## woody main [added with ubuntu-addons.bash_v060]
deb [http://www.micq.org/deb/](http://www.micq.org/deb/) woody main
 
## hoary evrmd-misc-stuff [added with ubuntu-addons.bash_v060]
deb [http://www2.fht-esslingen.de/~frbuit00/linux/debian-repo](http://www2.fht-esslingen.de/~frbuit00/linux/debian-repo) hoary evrmd-misc-stuff

----------------------------------------------

Have I picked up some dubious sources? Should I delete some of them?
If I do what will happen to the programs, will I be asked to 'downgrade'?

Cheers!

---

### Post by poofyhairguy on 2005-08-19
Thats the problem....your file is messed up. Make it look like this (only):

> ## Uncomment the following two lines to fetch updated software from the network
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

### Post by homersbrain on 2005-08-19
Right, I've edited the sources list to make it look like the one you sent me and software update confirms that the other sources have gone. However, in synaptic, firefox is still reading unsupported. Also the firefox gnome support is still the same. Do I need to uninstall my present version of firefox (and gnome support) and then will it pick up a new one? Advice would be much appreciated as I don't want to mess things up! Thanks.

---

### Post by sneax on 2005-08-19
Why do you need to install firefox? The latest version (1.0.6) is already installed as you said? I don't understand ...

---

