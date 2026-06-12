---
title: "Sources.list problems"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by whein on 2007-12-03
This has been bothering me for some time now.  I have two computers, one running Fiesty and one running Gutsy.  Both are using Synaptic to install/upgrade software.  Both are acting in ways I don't understand:

On my Fiesty box, my sources.list looks like this
```
deb ftp://ubuntu.mirrors.tds.net/ubuntu/ feisty main restricted multiverse universe
deb ftp://ubuntu.mirrors.tds.net/ubuntu/ feisty-updates main restricted multiverse universe
deb ftp://ubuntu.mirrors.tds.net/ubuntu/ feisty-backports main restricted multiverse universe
deb ftp://ubuntu.mirrors.tds.net/ubuntu/ feisty-proposed main restricted multiverse universe
deb http://security.ubuntu.com/ubuntu feisty-security main restricted multiverse universe

#IVTV driver
deb http://dl.ivtvdriver.org/ubuntu feisty all
```
but when I reload packages I get the following:
```
http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-amd64/Packages.gz: 404 Not Found
http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-amd64/Packages.gz: 404 Not Found
http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz: 404 Not Found
http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz: 404 Not Found

```
Why the heck is it trying to connect to medibuntu.sos-sts.com if that server is not in my sources.list???  Is there more than one location for sources.list that it looks at?  I took the above from /etc/apt/sources.list which I was led to believe was the one and only file I had to worry about for APT.

My box running Gutsy is having a similar, but slightly different problem.  The sources.list file on that machine looks like ```
deb ftp://ftp.grokthis.net/mirrors/ubuntu/ gutsy main restricted multiverse universe
deb ftp://ftp.grokthis.net/mirrors/ubuntu/ gutsy-updates main restricted multiverse universe
deb ftp://ftp.grokthis.net/mirrors/ubuntu/ gutsy-backports main restricted multiverse universe
deb ftp://ftp.grokthis.net/mirrors/ubuntu/ gutsy-proposed main restricted multiverse universe
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted multiverse universe

#Wine Repositories
deb http://wine.budgetdedicated.com/apt/ gutsy main

```
but when I reload packages on that machine I get ```
W: Duplicate sources.list entry http://wine.budgetdedicated.com gutsy/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_gutsy_main_binary-amd64_Packages)
```
I only have the Wine server listed once in /etc/apt/sources.list, but is there another directory/file (/var/lib/apt/lists/ ?) that APT looks at to pick servers?  I'm very confused.  :(

And since I'm on the topic of APT confusion, I've figured out how to add a single CD as a package source for APT, but is it possible to use two at the same time (one for Kubuntu and one for Ubuntu)?  What would the syntax of that be for the sources.list?
Thanks for any help you guys can give.
-Will

---

### Post by TameLion on 2007-12-03
I believe the old method for adding the medibuntu servers was to put them in a separate file in /etc/apt/sources.list.d/ (this directory is included in the apt sources)

As for the CD problem, the Kubuntu and Ubuntu CDs should have exactly the same packages on them as far as I know; it's just the defaults (Gnome or KDE) which are different.

---

### Post by Ptero-4 on 2007-12-03
Check your /etc/apt/sources.list.d/ folder. If there's anything in it, delete it and reload apt. Also, you can use apt-cdrom add to add any cd you want.

---

