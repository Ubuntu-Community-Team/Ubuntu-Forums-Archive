---
title: "Problems installing extra codecs."
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Tarvok on 2006-11-14
Hello. I've finally got my computer up and running (Dapper 6.06LTS, i386), downloading stuff over a dialup connection (ouch!). I'm currently trying to get extra codecs installed, and am running into trouble.

[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/codecs.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/codecs.html) tells me to install the following packages:

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg

bad-multiverse doesn't even seem to exist; I can't find it in Synaptic. ugly-multiverse is there, but when I attempt to select it, I get the following message:

"gstreamer0.10-plugins-ugly-multiverse:
 Depends: liblame0 (>=3.96.1-1) but it is not installable"

Any ideas?

---

### Post by pay on 2006-11-15
I think that you need to enable the multiverse repository. You can also install it by typing into the terminal ```
wget http://mirrors.kernel.org/ubuntu/pool/multiverse/l/lame/liblame0_3.96.1-1_i386.deb
sudo dpkg -i liblame0_3.96.1-1_i386.deb
```

---

### Post by Tarvok on 2006-11-15
Thanks for the snippet. I am now loading ugly-multiverse, though bad-multiverse is still MIA.

The thing is, so far as I know, I've enabled ALL repositories. I remember a few years ago when I had to edit a file manually to enable extra repositories, but I didn't think that was still the case. Actually, I've found a few more cases of unmet dependencies.

For example, I just got this message:

"totem-gstreamer-firefox-plugin:
  Depends: totem-gstreamer (=1.4.1-0ubuntu4) but 1.4.3-0ubuntu1 is to be installed"

The sun-java5-plugin package isn't on the list at all.

It really does look like I'm missing repositories, but so far as I can tell, they're ALL enabled. :confused:

---

### Post by pay on 2006-11-15
I normally use these repositories personally
```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list
```
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

# Repository for wine
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

```

---

### Post by Tarvok on 2006-11-15
Thanks, that seemes to have helped. I wonder why the defaults were so screwy?

---

### Post by hassan_saeed on 2006-11-15
You could also install _Automatix_. It is a great tool.
It helped me alot.

---

