---
title: "can't get beryl working..."
date: 2007-01-10
forum: Apple PPC Users
---

### Post by el-sio on 2007-01-10
Maybe I'm dumb...
Maybe I should sleep for a while and do it again
Maybe someone here will help me out of this ](*,) 

I try to install and run beryl on Ubuntu Edgy on a ibook G4 with ati mobility radeon 9200.
The 3D graphics work just fine, direct rendering is enabled.

when I try the official repo for beryl I can install it and running it make the windows border dissapear and I if I try to run beryl settings I get this :

```

** ERROR **: no d_ for a_active_plugins
aborting...
Abandon (core dumped)
```

I don't know if it is an error due to my system or to the package released...
So I tried svn packages...

And when I tried to install from the latest svn as described in [another topic]("http://www.ubuntuforums.org/showthread.php?t=279456&page=8&highlight=svn+beryl"), I can't retrieve the packages.

```

Unable to find expected entry beryl-svn/binary-powerpc/Packages in Meta-index file (malformed Release file ?)
```

Does anyone has a working beryl on PPC arch and could give me his (or her ;) ) source lsit ?
Actually I really want to know if the error comes from my system or from the package :(

---

### Post by Waappu on 2007-01-10
Hi

I used these guides and Beryl working great
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

I also added repo from here
[http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/)

---

### Post by el-sio on 2007-01-10
Thanks for your answer and howtos Waappu...

But I have the same problem again :/

I can't fetch the package from the svn repo :

I added the following in my source list :

```
deb http://ubuntu.beryl-project.org edgy main
deb http://beryl.limitless.lupine.me.uk edgy main
#deb http://mental-ppc.tuxfamily.org/dists edgy-mppc main incoming
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn
```

and I get this result :

```
Impossible de récupérer http://download.tuxfamily.org/3v1deb/dists/edgy/Release  Unable to find expected entry  beryl-svn/binary-powerpc/Packages in Meta-index file (malformed Release file?)
```

but still I can install beryl and emerald themes but when I launch it same error as always...

Then I removed totally beryl and its componensts (apt-get remove beryl emerald-themes and then apt-get autoremove), then I changed my source list to the following (as told in the beryl tutorial) :

```

deb http://ubuntu.beryl-project.org edgy main
deb http://3v1n0.tuxfamily.org edgy beryl-svn

```

and after update and dist-upgrade (with the same error about the malformed release file), it is impossible to get beryl !
```

Aucune version du paquet beryl n'est disponible, mais il existe dans la base
de données. Cela signifie en général que le paquet est manquant, qu'il est devenu obsolète
ou qu'il n'est disponible que sur une autre source
E: Aucun paquet ne correspond au paquet beryl

```

(it's in french but anyway it says that no vesion of the beryl package is available however it exists in the database which generally means that it is missing or obsolete or only available on another source)...

So either I get a buggy package (with beryl-settings not working) or no package at all...

There must be some kind of trouble with the PPC arch version on 3v1n0's repo... I should ask him...

---

### Post by Waappu on 2007-01-10
Hi

Could you post your source list?

---

### Post by el-sio on 2007-01-11
sure, here you go :

```
deb http://jp.archive.ubuntu.com/ubuntu/ edgy main restricted universe
deb-src http://jp.archive.ubuntu.com/ubuntu/ edgy main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://jp.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe
deb-src http://jp.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://jp.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://jp.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://jp.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://jp.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://ubuntu.beryl-project.org edgy main
#deb http://beryl.limitless.lupine.me.uk edgy main
#deb http://mental-ppc.tuxfamily.org/dists edgy-mppc main incoming
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn
```

with this source list, I can't fetch ANY beryl packet and I&#12288;receive the error about the malformed release file on 3v1n0 repos...

What does your apt sourcelist look like ?

Thank you for your help.

EDIT : by the way, if I&#12288;uncomment those lines :

```
#deb http://beryl.limitless.lupine.me.uk edgy main
#deb http://mental-ppc.tuxfamily.org/dists edgy-mppc main incoming
```

I can install beryl and emerald-themes, but beryl setting crashes with the "no d_ for a_active_plugins" error...

---

### Post by Waappu on 2007-01-11
Hi

My source list is quite same.

You are already find problem that ppc package is missing from repo.
[http://www.ubuntuforums.org/showthread.php?p=1988064](http://www.ubuntuforums.org/showthread.php?p=1988064)
I hope you find find solution to that and maybe I can't help after that

---

### Post by GermanFafian on 2007-01-11
Have you tried installing Automatix bleeder?
  It has the option to install Beryl. 
It worked in my NVidia machine too bad my ATi fitted laptop refuses to run  Beryl ](*,)

---

### Post by el-sio on 2007-01-11
Which package should I install for automatix ?
I cant find nothing corresponding to automatix either with synaptics nor manually through apt-get install...

Is it available on PPC architecture ?

Thanks for the help anyway...

---

### Post by GermanFafian on 2007-01-11
> **el-sio said:**
> Which package should I install for automatix ?
I cant find nothing corresponding to automatix either with synaptics nor manually through apt-get install...

Is it available on PPC architecture ?

Thanks for the help anyway...

 Ooops! I had no idea what what kind of equipment automatix bleeder worked on.
  You can always try the traditional way as I installed it that way in a friend's PC. When it failed the first time I just uninstalled everything and started from scratch.
  Anyway. Here is the page where automatix is.
  [http://www.getautomatix.com]("http://www.getautomatix.com")

---

### Post by el-sio on 2007-01-11
PROBLEM&#12288;SOLVED (using SVN source to make my own debs)

---

### Post by GermanFafian on 2007-01-11
> **el-sio said:**
> PROBLEM&#12288;SOLVED (using SVN source to make my own debs)
Great.
Now help me get it running in my ATI laptop :biggrin: 
 Just kidding ;) 
 Glad you sorted it out.

---

