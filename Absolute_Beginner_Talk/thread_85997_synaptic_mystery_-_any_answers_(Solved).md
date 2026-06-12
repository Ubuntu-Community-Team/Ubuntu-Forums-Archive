---
title: "synaptic mystery - any answers? (Solved)"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by Jake version 2.0 on 2005-11-04
Hi all.  I'm new to the forum.  My name is Jake, but there was already a Jake here so I'm going by "Jake version 2.0" on this forum.


HERE'S SOME HISTORY/INFO ABOUT ME
(skip to below, if you just want to get to the Synaptic Mystery)

I'm a long time computer user, all the way back to Trash80.  I've had Apples, Commodores, Amigas, 3COM Audreys and PCs.  Still have my Amiga 2000.  I'm just getting rollin' in Linux.  Tried Red Hat about 7 years ago, but dropped it after 6 months due to more pressing computer issues in the Windows/Novell system I was admin of.  Recently, I moved our company from Novell to MS Server 2003.  More recently, I hired a company to install a 1 terabyte Ubuntu server at my office and another one at my home, hooked together through a T1.  I also have an additional Ubuntu server at home to experiment with.  We run our website, email, ftp, etc. on the office server then the office server auto backups to the home server.  It pretty k00l.  So... now I need to become "Super Linux Guru!".  I'm gathering books, websites and people to help me get from here to there.




======================
HERE'S THE SYNAPTIC MYSTERY

First know that I have 3 Ubuntu servers. One at my office.  One at my home.  And one at my home that I use to experiment with.

I copied my "/etc/apt/sources.list" from my office Ubuntu server to my home experimental Ubuntu server.

On my office server I can find/download/install "smeg" using Synaptic.

On my home experimental server it doesn't even show up in the list, even thought I copied the "/etc/apt/sources.list", and when I display the repositories, they look identical to the ones I have at work.

QUESTION:  What am I missing here?

---

### Post by aysiu on 2005-11-04
Post your /etc/apt/sources.list here, and we'll take a look. Welcome, by the way.

---

### Post by Jake version 2.0 on 2005-11-04
Thanks for the reply, here's the "source.list" file content...


##wing two lines to fetch updated software from the network
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
#deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
#deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

---

### Post by aysiu on 2005-11-04
I think it may be in the Hoary backports. Follow these directions:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

Then, type this in a terminal ```
sudo apt-get update
sudo apt-get install smeg
``` Any luck? Can you post the output of that?

---

### Post by Jake version 2.0 on 2005-11-04
Thanks again for the reply and the links.  I edited "source.list", did the update and the install.  Still not working.  Here's the screen output...



root@u1home:/etc/apt # apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Fetched 5B in 5s (1B/s)
Reading package lists... Done
root@u1home:/etc/apt # apt-get install smeg
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package smeg
root@u1home:/etc/apt #

---

### Post by aysiu on 2005-11-04
Well I did a [Ubuntu packages search](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=smeg&searchon=names&subword=1&version=all&release=all), and it appears SMEG is just not available for Hoary. It's in Breezy and Dapper.

You can download the SMEG .deb file from [here](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fs%2Fsmeg%2Fsmeg_0.7.5-0ubuntu2_all.deb&md5sum=54c62ef80ee7813a26f0f49aed6b4339&arch=all&type=main) to your desktop. Then ```
cd Desktop
sudo dpkg -i smeg_0.7.5-0ubuntu2_all.deb
```

---

### Post by Jake version 2.0 on 2005-11-04
many... Many... MANY THANKS for the replies, aysiu.  I'll get "smeg" by downloading or whatever.  I just thought it was very weIRd that "smeg" shows up on my office machine but not on my home machine, even though both of them have the same "sources.list".  One of those things that make you go Hmmmmmm.   Anyway... thanks again! :smile:

---

### Post by Jake version 2.0 on 2005-11-08
Tried installing SMEG with...

```
sudo dpkg -i smeg_0.7.5-0ubuntu2_all.deb
```

got the following error...

```
dpkg: dependency problems prevent configuration of smeg:
 smeg depends on python-xdg (>= 0.14); however:
  Version of python-xdg on system is 0.9-1.
dpkg: error processing smeg (--install):
 dependency problems - leaving unconfigured
```

so... I reading this two ways... 1, my version of python-xdg is too new to work with smeg and 2, I just need to do a LOT more studying and working with linux.  I am not there yet.

Thanks for all the replies and help.  I will continue to continue on,  until I get a better handle on all this.

---

### Post by aysiu on 2005-11-08
[QUOTE=Jake version 2.0]1, my version of python-xdg is too new to work with smeg[/QUOTE] Actually, it's too *old*. If that's the only dependency problem, you can try manually installing [the newer version of python-xdg](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fp%2Fpyxdg%2Fpython-xdg_0.15-0ubuntu1_all.deb&md5sum=029298ce9c0b0cad1eb31fbcdb78fa05&arch=all&type=main).

---

### Post by Jake version 2.0 on 2005-11-08
Opps!  looked at .9 vs .14, brain seen .9 vs .1.4.  Bad brain!  Installed the update to Phython from the link you provided.  Then installed SMEG.  I'm SMEG'n now.  Thanks!:smile: 

I'll have to do some thinking about the whole dependency thing.  Sounds like that might get into a lot of domino effect.

---

### Post by Jake version 2.0 on 2005-11-09
Ahhh... my original puzzlement :confused: has been resolved.  Originally I was puzzled as to WHY SMEG would show up on my Synaptic list on my office Ubuntu but not at my home Ubuntu, even though they had the same "sources.list" file.  Now that SMEG is INSTALLED on my home Ubuntu, it does show up in the Synaptic list.  So... it seems that even if SMEG is not in one of the repositories in the "sources.list" file, it will still be listed in Synaptic if it is already installed.

One mystery down, 9,999,999 to go.

---

