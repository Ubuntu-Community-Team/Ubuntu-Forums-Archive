---
title: "Synaptic"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by Matt Houston on 2005-11-15
Total newbie question here re Synaptic

Trying add universe and multiverse following the Ubuntu Start Guide, I have followed it all word for word, but n step six it says you should now see that all the repository's should now be checked, which they are not. 

If i select Skype for instance on the left it says 'no package selected' on the right, I've run through this five times now, any ideas?

---

### Post by Mustard on 2005-11-15
I don't think skype is available through the standard ubuntu repositories.

Try this guide for skype;

[Skype HOW TO]("http://www.ubuntulinux.org/wiki/SkypeHowto/")

The issue of whether your universe and multiverse are enabled would be diagnosed best if you copied and pasted your sources.list into this thread.

To see your sources.list try this;

```
cat /etc/apt/sources.list
```

---

### Post by Matt Houston on 2005-11-15
Here you go:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main r estricted


## Uncomment the following two lines to fetch updated software from the network
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe main restricted multiver se
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted univer se multiverse
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted un iverse multiverse

 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted m ultiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by Mustard on 2005-11-15
Hmmm...it looks a bit messy. :)

I'm not sure whether those spaces in 'multiver se' are due to a forum glitch or whether they are present in your actual sources.list or not.  A tip for the future would be that you can enclose code inside these [noparse]```
 
```[/noparse] and it will display them in your forum post correctly.

Might I suggest you copy and paste this sources.list below entitled NEW SOURCES.LIST, over the top of your old sources.list and completely replace it, using this command below to edit the file;

```
sudo gedit /etc/apt/sources.list
```

When you have copied over your old sources.list with the new one (shown below) then save the file and run this command;

```
sudo apt-get update   

#NOTE:Synaptic needs to be closed when running certain apt-get commands or you will receive a lock file error.
```


NEW SOURCES.LIST;
```

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic

# Ubuntu supported packages (packages)
deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources)
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages)
deb http://gb.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu breezy-security universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-updates universe multiverse

# Ubuntu community supported packages (sources)
deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-updates universe multiverse
```

NOTE:I haven't included breezy backports in this new sources.list.  When there is an official announcement about breezy backports being open, then you can add that as well.  For now I would keep it disabled.

---

### Post by Matt Houston on 2005-11-16
Look slike that did the trick, cheers mate.

---

