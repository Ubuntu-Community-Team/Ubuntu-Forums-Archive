---
title: "Help! I broke Synaptic Package Manager"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by UberIcarus on 2006-07-17
I was trying to add PLF repositories to my computer and now I get this:

 Type 'eb' is not known on line 23 in source list /etc/apt/sources.list
E: The list of sources could not be read.

I removed ALL repositories, and then added them again. Same thing. I also get  an unable to lock message

I have NO packages anymore.

---

### Post by PriceChild on 2006-07-17
The unable to lock is from two package managers simultaneously open.

If i were you, i would make a blank sources list, and then add one repository at a time in synaptic to find out which one's giving you the problem.

---

### Post by givré on 2006-07-17
Let see your /etc/apt/sources.list

---

### Post by UberIcarus on 2006-07-17
Okay, figured out that it was a problem with my sources list...however now I  can't edit my sources list. Tried using gksudo, and even running from root.

here's the list:

## Major bug fix updates produced after the final release of the
## distribution.

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


eb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

deb [ftp://ftp.planetmirror.com/pub/plf/ubuntu/plf/dists/dapper/free/binary-i386](ftp://ftp.planetmirror.com/pub/plf/ubuntu/plf/dists/dapper/free/binary-i386)
deb [ftp://ftp.planetmirror.com/pub/plf/ubuntu/plf/dists/dapper/non-free/binary-i386](ftp://ftp.planetmirror.com/pub/plf/ubuntu/plf/dists/dapper/non-free/binary-i386)
deb [ftp://ftp.planetmirror.com/pub/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/](ftp://ftp.planetmirror.com/pub/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/)
deb [ftp://ftp.planetmirror.com/pub/plf/ubuntu/plf/dists/dapper/free/binary-i386](ftp://ftp.planetmirror.com/pub/plf/ubuntu/plf/dists/dapper/free/binary-i386)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

---

### Post by Dinerty on 2006-07-17
Hey mate, if you want a quick fix to this problem, then try this

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

**Writteb by **lordlolol**


Well, before clear anything, try this
 
 
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```


 So you have ex exact copy of your messed up repo file.
 
 Then from a terminal
 
 
```

gksudo gedit /etc/apt/sources.list
```

 and replace all the lines with your brand new sources.list as provided from the site I linked. Save the file and close the editor.
 
 Now
 
 
```

sudo apt-get update
```

 Now eveything should work. If this is not the case, you can restore your old sources.list (even if it is screwed)...




This basically allows you to get your basic repo's back mate

---

### Post by Skia_42 on 2006-07-17
To edit the source list, use:
> sudo gedit /etc/apt/sources.list
This is my source list, backup the original if you make any changes:
> # deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


---

### Post by UberIcarus on 2006-07-17
Whoa! cool. I fixed it myself. I edited out the duplicates, and then added the necissary universe multiverse after it.

:) I'm learning fast. I don't think I'd have this much success using windows. LoL

gedit didn't work for me, so I used sudo nano

---

### Post by givré on 2006-07-17
> **UberIcarus said:**
> 
eb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

This is the problem. Just remplace this line by
```
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
```

---

### Post by Skia_42 on 2006-07-17
Nice job.

---

