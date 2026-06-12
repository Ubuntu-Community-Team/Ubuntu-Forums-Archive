---
title: "Synaptic Package Manager"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by LiquidFlame on 2006-04-19
So I was follwoing a guide to install MPlayer and it worked fine and runs great.  I got the guide from here: [http://ubuntuguide.org/]("http://ubuntuguide.org/") but in the guide it had me add extra repositories.  I just noticed that I'm using Ubuntu 5.10 "Breezy Badger and the repositories that the guide had me add I think are for a differnt version.  My friend said this is a bad idea beacuse it can mess up your kernal.  So does any one know the orignal repositories I should have or what repositories I should have in my synaptic package manager?  Any help would be great.  Oh by the way this is what I have right now in my sources.list.

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

### Post by aysiu on 2006-04-19
See this:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Madpilot on 2006-04-19
Ubuntuguide.org is quite out of date, and really should be avoided.

the Mirrormax Ubuntu-backports repos have been gone for nearly six months, for example, but they're still mentioned in ubuntuguide... Also, that sources.list you pasted above is for 5.04 (Hoary), not 5.10 (Breezy)!

Try this for an official sources.list: [http://paste.ubuntu-nl.org/6047](http://paste.ubuntu-nl.org/6047)

And for more information: [http://wiki.ubuntu.com/AddingRepositoriesHowto](http://wiki.ubuntu.com/AddingRepositoriesHowto)

---

