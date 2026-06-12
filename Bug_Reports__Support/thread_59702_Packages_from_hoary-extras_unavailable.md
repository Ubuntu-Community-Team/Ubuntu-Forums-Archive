---
title: "Packages from hoary-extras unavailable"
date: 2005-08-25
forum: Bug Reports / Support
---

### Post by auer on 2005-08-25
Hi,
I can't install any packages from hoary-extras, eg j2re. I just installed Ubuntu on my working PC, so it is a freshly installed version of Hoary. The hoary-extras is added to the sources.list file (I already tried other mirrors, but it doesn't work). When calling apt-get update, it produces the following output:

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Get:5 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages [2490B]
Get:6 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages [2411 B]
Get:7 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages [33 B]
Get:8 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages [48 85B]
Fetched 9823B in 1s (8770B/s)
Reading package lists... Done

With my sources.list:
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
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Searching for j2re with apt-cache does not find any packages, and installing acroread install the 5.0 version from hoary.

---

### Post by sbassett on 2005-08-25
Has there been any word on this as of yet?? I have gone through the forums and cannot seem to find any other word. All hoary-extra packages are being ignored through the apt-get update. This has happened with 2 fresh installs.

---

### Post by veratyr on 2005-08-25
Having similar problems after a fresh install of hoary. When I try and install the java runtime it says it can't find the package. Synaptic aslo complains that it can't update gaim, gimp, mozilla-firefox, samba-common. I find it strange that it would want to update firefox cause I seem to have 1.0.6 installed from backports. I hope this is fixed soon.

---

### Post by acascianelli on 2005-08-25
[http://www.ubuntuforums.org/showthread.php?t=59780](http://www.ubuntuforums.org/showthread.php?t=59780)

I'm having the same problem.  Best answer I get is just wait till the backport admins get it fixed...Good enough for me, as long as I know its not a problem with my system.

---

### Post by incinerator on 2005-08-25
It seems the Packages.gz files are missing some of the packages, for example sun-j2re. The package is in the right directory on the download server but as Packages.gz does not contain a reference to it, it won't be seen by apt. Something seems to go wrong when these Packages.gz files get generated.

---

### Post by acascianelli on 2005-08-25
Backports are the same way.

---

### Post by cyrix on 2005-08-25
I guess we aren't going to get an answer back and or the packages installed. Other than the packages not being present this is a killer OS. BUT, alas I can't swicth over to this flavor of linux until I can at least do the basics like get java to install.

I have my own servers f**k it, I'll donate some space or a server to store these packages. I am sitting on a gigabit connection peered with Time Warner as well, with my own switches, backups and UPS. Let me know...

---

### Post by veratyr on 2005-08-25
hrm I switched from the mirrormax backports to the official backports and it fixed gaim, gimp, mozilla-firefox, and samba-common from not upgrading but I still can't install java. I guess extras is still screwed up.

---

### Post by rpgcyco on 2005-08-26
> but I still can't install java. I guess extras is still screwed up.

According to the [announcement thread](http://ubuntuforums.org/showthread.php?t=52168), extras were never added to the Official Backports. :(

So I guess we're stuck until the unofficial repos are fixed. :(

- Rpg Cyco

---

### Post by c0rderr0y on 2005-08-26
this makes me sad..... very sad.... i'm afriad im going to have to use a different linux if this doesnt get fixed soon and this will also discourage a lot of new users.

---

### Post by sbassett on 2005-08-26
Well, if the official servers are not fixed by a.m. tomorrow, I will be submitting my own. I have been syncing a section of my servers off the backports/extras and creating my own repos. Have worked peachy for me. I would be glad to share with all that don't mind an 80 KB/s limit.

---

### Post by sbassett on 2005-08-27
deb [http://bassett.homelinux.org:81/ubuntu/DEBS/](http://bassett.homelinux.org:81/ubuntu/DEBS/) /

---

### Post by sal on 2005-08-27
thank you verry much for this.

---

### Post by acascianelli on 2005-08-28
Everything seems to be fixed now for me.  Anybody else want to confirm this also?

---

### Post by incinerator on 2005-08-28
Yup, the Packages.gz files seem to have been fixed. However, now my proxy dns server doesn't resolve ubuntu-backports.mirrormax.net anymore. Not a big problem though, just using planetmirror for now.

---

### Post by ShaneAu on 2005-08-28
[QUOTE=incinerator]Yup, the Packages.gz files seem to have been fixed. However, now my proxy dns server doesn't resolve ubuntu-backports.mirrormax.net anymore. Not a big problem though, just using planetmirror for now.[/QUOTE]

Force reload (Ctrl Reload). I was playing around with DNS records.

---

### Post by incinerator on 2005-08-28
In my case the problem is with my ISP, their dns proxy hasn't been updated so far. It may take a while for the changes to propagate. Anyways, thanks for the info.

---

