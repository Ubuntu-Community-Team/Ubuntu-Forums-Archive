---
title: "&quot;Cannot install all availale updates&quot; msg by every update, why?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by stoer on 2007-01-12
Hi All,

For a couple of weeks now i get the following warning whenever there is a update availale.

"Cannot install all available updates".see scrn shot.

I changed my sources list a while back, other than that, i'm unsure as to why i'm getting the message each time.

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

# deb http://packages.freecontrib.org/plf/ dapper free non-free
# deb-src http://packages.freecontrib.org/plf/ dapper free non-free

```

Anybody see where i've got it wrong?

---

### Post by rai4shu2 on 2007-01-12
It's holding back updating "checkinstall" probably because you have an old "installwatch" in your system. My guess is you need to remove both of those, then reinstall checkinstall.

---

### Post by fsando on 2007-01-12
Hope I can help as I am quite new to linux
I've had problems that seem similar. For one problem I needed the gpg-key for the server. As I did it I found the a link to that key somewhere (I found link to repo + key in various tutorials) - There is probably a more official way to get repo/key links.
The key is imported with a command **wget** (see link below).
Second problem was that from one server was serving  corrupted files, so I added a mirror. Again I perused the tutorials and found a mirror to add. Apparently synaptic figured out to get the packages where they were not corrupted.
In my case the problem server was the [[COLOR="Blue"]Beryl Project[/COLOR]]("http://ubuntu.beryl-project.org").
Though this is a [COLOR="RoyalBlue"][  [COLOR="Blue"]Tutorial on installing Beryl[/COLOR]]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")[/COLOR] it gives some hints on adding repo-sources and keys.
As aside today **apt-get update** gave me gpg errors from all beryl related servers (I have 3 in my list).

---

### Post by STREETURCHINE on 2007-01-12
> **fsando said:**
> Hope I can help as I am quite new to linux
I've had problems that seem similar. For one problem I needed the gpg-key for the server. As I did it I found the a link to that key somewhere (I found link to repo + key in various tutorials) - There is probably a more official way to get repo/key links.
The key is imported with a command **wget** (see link below).
Second problem was that from one server was serving  corrupted files, so I added a mirror. Again I perused the tutorials and found a mirror to add. Apparently synaptic figured out to get the packages where they were not corrupted.
In my case the problem server was the [[COLOR="Blue"]Beryl Project[/COLOR]]("http://ubuntu.beryl-project.org").
Though this is a [COLOR="RoyalBlue"][  [COLOR="Blue"]Tutorial on installing Beryl[/COLOR]]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")[/COLOR] it gives some hints on adding repo-sources and keys.
As aside today **apt-get update** gave me gpg errors from all beryl related servers (I have 3 in my list).







i have the same on edgy from todays updates 3 from beryl wont install wrong size or something.thought it was just me..lol

---

### Post by stoer on 2007-01-12
Thanks for your replies.

Only i can't work out why "installwatch"/"checkinstall" worked without a problem for so long, and now not. If installwatch was an old version wouldn't it have caused problems before? :-k 

Still think i pooched something in my sources list...

What will be the efeect of uninstalling/reiinstalling  installwatch and checkinstall, do i lose anything by doing this?

---

### Post by rai4shu2 on 2007-01-12
The new checkinstall has some cosmetic feature improvements and some (IHMO) fixes. Plus it isn't over 2 years old, like the old one.

---

### Post by STREETURCHINE on 2007-01-12
> **stoer said:**
> Thanks for your replies.

Only i can't work out why "installwatch"/"checkinstall" worked without a problem for so long, and now not. If installwatch was an old version wouldn't it have caused problems before? :-k 

Still think i pooched something in my sources list...

What will be the efeect of uninstalling/reiinstalling  installwatch and checkinstall, do i lose anything by doing this?

you'r source list is fine ,the problem is not there.try uninstalling installwatch and install checkinstall

---

### Post by stoer on 2007-01-12
Ok, uninstalled installwatch and installed checkinstall.

Everything looks good,

Thanks all for the help, much appreciated.

---

### Post by STREETURCHINE on 2007-01-12
not a problem,,,:-D

---

