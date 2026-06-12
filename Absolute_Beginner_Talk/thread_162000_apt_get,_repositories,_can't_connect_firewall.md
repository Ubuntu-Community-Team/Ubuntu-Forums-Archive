---
title: "apt get, repositories, can't connect? firewall?"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-04-18
Hello,
Firstly sorry if this has been posted before I didnt manage to find anything on the wiki.
I'm trying to install some new software (java and eclipse) using apt get , or the synaptic thingy (sorry im posting this from a windows machine and cant remember the name of it).
It doesn't seem to be able to connect to the repositories, I get a message saying something like "connecting to the such and such failed".

I can browse the web fine using firefox, I can ping other machines on my network, but I'm behind a proxy/firewall that requires authentication would this be stopping the connection to the repositories? 

Can anyone help?

Thanks in advance!

---

### Post by meborc on 2006-04-18
there might be smthing wrong with your sources.list file... can you post your sources.list? 

**sudo gedit /etc/apt/sources.list**

and copy it here

---

### Post by bplus on 2006-04-18
> 
restricted
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports universe multiverse
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe multiverse

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) breezy universe multiverse


thanks!

---

### Post by meborc on 2006-04-18
it looks good... there has been some issues of timing (apt problem)... it is quite rare as i have never had it... but the workaround or fix was smthing like refreshing from synaptic or commenting (#) out all the lines in sources.list and then updateing... then again remove the # you inserted... ahh... there was a thread, but it was a while ago and i can't find it... srry ... but the list looks good :mrgreen:

try this -
[http://ubuntuforums.org/showthread.php?t=123866](http://ubuntuforums.org/showthread.php?t=123866)

---

### Post by bplus on 2006-04-18
Hi,
thanks for that, I looked at the thread you suggested but the guy sorted it out by setting his proxy up, I ve done that using the same settings i ve got in firefox (firefox works) but still it cant download packages. Are the packages downloaded using UDP? I think thats blocked by my proxy.............

I ve noticed that during start up of ubuntu, it says it fails to sink with unix clock (the one with a web address, would this be a related issue?

Thanks again!

---

### Post by suitti on 2007-12-12
I've been running FIesty Fawn at work.  There's a firewall, but i'd gotten the right noise into Firefox, an environment variable that takes care of wget, and /etc/apt.conf has noise for apt-get, if not synaptic.

I'm installing Gutsy on a new box.  The Firefox and wget noise work fine.  But I can't get apt-get or synaptic to talk to me.  The man page for apt.conf looks as if they've changed the format from a simple one-liner to an xml format.  There's a sample config file, but it doesn't have enough in it to let me know what they're expecting.

Neither apt-get nor synaptic seem to issue any kind of error or warning that might point me anywhere.

I'm installing Gutsy at home, but there's no firewall.  Just a slow modem.  It's taking forever.  I'd really prefer to get everything on a DVD set somehow.  Are there repositories in DVD ISO format that can be downloaded?  I'm grasping at straws here.

---

### Post by skymera on 2007-12-12
is see your using Breezy? very old.

any reason for such an old version? just curious.

and havent updates stopped for breezy =S

---

### Post by jken146 on 2007-12-12
I believe there is a howto somewhere on these forums for DVD repos.

---

