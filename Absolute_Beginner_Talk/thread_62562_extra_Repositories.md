---
title: "extra Repositories"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-09-05
Hi,

As some of you know i have had not found it straightforward getting extra repositories. Naturally i want to have maximum resources available. Initially i follwed the synaptic route to getting extra repositories following this wiki link: 
 [https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29)

this got my total of packages up to 16,316 

I have not followed this wiki guide: 
[https://wiki.ubuntu.com/AddingMultimediaRepositories?highlight=%28repositories%29](https://wiki.ubuntu.com/AddingMultimediaRepositories?highlight=%28repositories%29)

and now my total list of packages on Synaptic shows 16, 379!

Clearly there is more than one way of skinning this cat (sorry, cats - its just an expression) Not just that different methods yield different results. 

However, as a consequence of following the second procedure i got this:
"the following problems were found" :

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)


I would be very grateful if someone can give my sourcelist a once-over tell me what may be causing the problem. Like i said i want to max my resource potential, i.e. have as many packages available on Syanptic as possible but without causing problems too.



My source list:


sudo gedit /etc/apt/sources.list:

## Uncomment the following two lines to fetch updated software from the network
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

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

#Hoary-Extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted



## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted



Thanking in advance,


--
sophtpaw

---

### Post by frodon on 2005-09-05
Do you really know why you're using [BACKPORT](https://wiki.ubuntu.com/UbuntuBackports?highlight=%28backport%29)  repositories ? (it might be dangerous if you don't know why you're using [BACKPORTS](http://www.ubuntuforums.org/showthread.php?t=45047&highlight=backport) ).

---

