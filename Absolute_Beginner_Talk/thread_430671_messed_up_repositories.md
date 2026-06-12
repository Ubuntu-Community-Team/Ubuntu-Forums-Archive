---
title: "messed up repositories"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by SVWander on 2007-05-02
Trying to get Feisty Fawn to work and I think I have screwed up my repositories and I am not sure which ones to add. I just now ran:  cat /etc/apt/sources.list 

deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx
deb-src [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe multiverse
#AUTOMATIX REPOS END
## E17 repository "edevelop.org"
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

I am trying to install codecs, camerorama and EasyCam2 but get this error message when trying to add or remove anything:

[B]
E: privoxy: subprocess post-installation script returned error exit status 1[/B]

Can anyone tell me which repositories I need?

---

### Post by taurus on 2007-05-02
What the heck!  You have three different releases in your /etc/apt/sources.list at the same time!  That is a sure way to screw up your machine big time.  Are you running Feisty right now?  I recommend you start a new /etc/apt/sources.list.

```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main 

```
Save the new one, then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by SVWander on 2007-05-02
I copied the sites into apt/sources.list as listed in your message then ran aptitude update and aptitude upgrade. When running upgrade I get the following error:

tim@tim-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up privoxy (3.0.6-1) ...
chown: `privoxy.adm': invalid user
dpkg: error processing privoxy (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 privoxy
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up privoxy (3.0.6-1) ...
chown: `privoxy.adm': invalid user
dpkg: error processing privoxy (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 privoxy

---

### Post by starcraft.man on 2007-05-02
Did you try to install Tor (The Onion Router) before you changed your messed up repos to Feisty? Privoxy is the client used to hide your browsing in firefox, and only reason to have it is in conjunction with tor... I do not really know what the error messages mean though, maybe you downloaded an outdated version from old repos and it was incompatible >.> and if you didn't try to get tor working before, I don't know why it would automatically install with the upgrade command. Anyone know?

---

### Post by SVWander on 2007-05-03
> **starcraft.man said:**
> Did you try to install Tor (The Onion Router) before you changed your messed up repos to Feisty? Privoxy is the client used to hide your browsing in firefox, and only reason to have it is in conjunction with tor... I do not really know what the error messages mean though, maybe you downloaded an outdated version from old repos and it was incompatible >.> and if you didn't try to get tor working before, I don't know why it would automatically install with the upgrade command. Anyone know?

Yes, for some reason TOR is installed. But I cannot uninstall anything with Synaptic Package Manager because I get that error message. TM

I tried again to install a program just to catch the error message. There was no way to copy the display in the terminal so I wrote it down. It might not be completely actuate. As you stated Starcraft it has something to do with the proxy that I tried to install months and months ago . . . but has never given me any problems. The terminal reads the following:

[COLOR="Blue"]Setting up privoxy (3.0.6-1) . . . 
chown: privoxy.adm': invalid user
dpkg: error processing privozy (--configure)
   subprocess post-installation script returned error exit status 1
Error were encountered while processing:
Privoxy
E: sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up privoxy (3.0.6-1) . . . 
chown: privozy.adm' :invalid user
dpkg error processing privoxy (--configure)
  Subprocess post-installation script returned error exit status 1
[/COLOR]

I hope someone can help me figure out what's going on so I don't have to reinstall Ubuntu. I don't even like booting into XP anymore . . .

---

