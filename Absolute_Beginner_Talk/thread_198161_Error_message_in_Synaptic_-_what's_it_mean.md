---
title: "Error message in Synaptic - what's it mean?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2006-06-16
I'm a Breezy user, waiting for CDs from shipit so I can move to Dapper.  But I still want to fix a problem I've got in Synaptic. I don't know Synaptic very well - I've got the point and clicking straight in my head.  But when I start Synaptic I get this error message in a dialogue box:

> The following problems were found on your system

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)


What does it mean? And how do I fix it?

It doesn't seem to affect Synaptic's functionality; but I don't use it much, so there could be a fault that I just haven't come across yet.  So I want to fix it... just in case, y'know?

---

### Post by rado_london on 2006-06-16
I would say that your sources.list are wrong. Can you post the output of 
```
cat /etc/apt/sources.list
```

---

### Post by dcstar on 2006-06-17
[QUOTE=gr0kzer0]I'm a Breezy user, waiting for CDs from shipit so I can move to Dapper.  But I still want to fix a problem I've got in Synaptic. I don't know Synaptic very well - I've got the point and clicking straight in my head.  But when I start Synaptic I get this error message in a dialogue box:



What does it mean? And how do I fix it?

It doesn't seem to affect Synaptic's functionality; but I don't use it much, so there could be a fault that I just haven't come across yet.  So I want to fix it... just in case, y'know?[/QUOTE]
The first messages say that you do not have your Breezy CD in your drive, the last two messages say that you cannot contact the gb.ubuntu mirror site.

Go into Synaptic and edit your Repositories to remove the CD, and edit out the "gb." part out of the other setting as sometimes these mirror sites are unreliable (or check your Synaptic proxy settings).

---

### Post by gr0kzer0 on 2006-06-17
Rado_london, here's my sources.list:

> 
t0p@lapt0p:~$ cat /etc/apt/sources.list
 deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
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
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


Dcstar, when you say "edit out the GB", I take it you mean so, for example,

>  deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

becomes

> deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

Thanks for the help guys!

---

### Post by dcstar on 2006-06-17
[QUOTE=gr0kzer0]
.....
Dcstar, when you say "edit out the GB", I take it you mean so, for example,
.....
Thanks for the help guys![/QUOTE]
Yep, got it in one!

---

