---
title: "Java problems?"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by rj686 on 2005-09-16
Ok i tried breezy but no matter what i did i couldn't get firefox to recognize java, it was listed and installed using synaptic i tried reinstall it didn't help. I sought outside help but he couldn't figure what was wrong all the links were in the right places. Azureus ran but limewire didn't. The java test page said i didn't have any java in my computer.  Now im gonna try hoary to see if that works. Is anyone else running Ubuntu breezy and does your java work? i've run out of ideas

---

### Post by rj686 on 2005-09-16
i even tried making a package out of the sun-java binary, it worked successfully but still no java support in firefox. Can anyone help me?

---

### Post by Kapre on 2005-09-16
[QUOTE=rj686]i even tried making a package out of the sun-java binary, it worked successfully but still no java support in firefox. Can anyone help me?[/QUOTE]

I'm using ubuntu and is running java (sunjava re1.5). I've encountered the same problem you're having  when I installed it. What I did to get the java was to add the hoary universe/multiverse in my repo list.

K

---

### Post by rj686 on 2005-09-16
[QUOTE=Kapre]I'm using ubuntu and is running java (sunjava re1.5). I've encountered the same problem you're having  when I installed it. What I did to get the java was to add the hoary universe/multiverse in my repo list.

K[/QUOTE]
  ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

##Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted



there is my repo list do i have all of em. Like i said i FOUND the package when i use synaptic it just doesnt do anything...i added the repos but still nuthin

---

### Post by padre999 on 2006-06-06
[https://wiki.ubuntu.com/RestrictedFormats#head-ef347c277a133b64af0600bd1bf24bc64e7038b8](https://wiki.ubuntu.com/RestrictedFormats#head-ef347c277a133b64af0600bd1bf24bc64e7038b8)

---

