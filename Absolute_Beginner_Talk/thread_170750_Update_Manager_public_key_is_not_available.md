---
title: "Update Manager: public key is not available"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-05-05
While trying to run update manager, it gave me this error:

The following problems were found on your system:

W: GPG error: [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E8DDB29170188C3B
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088

What's wrong? why kubuntu? I am using ubuntu!!!!! and what is the public ker? PLEASE HELP!!!

---

### Post by Isoss on 2006-05-05
Also when I try Terminal: sudo apt-get update, the output goes like this:
```
isos@ubuntu:~$ sudo apt-get update Ign http://theli.free.fr ./ Release.gpg
Get:1 http://koti.mbnet.fi breezy/ Release.gpg [65B]
Ign http://wine.lowvoice.nl breezy Release.gpg
Get:2 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:4 http://kubuntu.org breezy Release.gpg [189B]
Hit http://wine.lowvoice.nl breezy Release
Ign http://theli.free.fr ./ Release
Hit http://koti.mbnet.fi breezy/ Release
Ign http://koti.mbnet.fi breezy/ Release
Hit http://security.ubuntu.com breezy-security Release
Ign http://wine.lowvoice.nl breezy/main Packages
Get:5 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Ign http://deb.opera.com etch Release.gpg
Ign http://theli.free.fr ./ Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Ign http://wine.lowvoice.nl breezy/main Sources
Ign http://koti.mbnet.fi breezy/ Packages
Get:6 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://wine.lowvoice.nl breezy/main Packages
Hit http://theli.free.fr ./ Packages
Hit http://kubuntu.org breezy Release
Ign http://kubuntu.org breezy Release
Hit http://archive.ubuntu.com breezy Release
Ign http://koti.mbnet.fi breezy/ Sources
Hit http://wine.lowvoice.nl breezy/main Sources
Hit http://archive.ubuntu.com breezy-updates Release
Ign http://deb.opera.com etch Release
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://koti.mbnet.fi breezy/ Packages
Hit http://archive.ubuntu.com breezy-backports Release
Hit http://kubuntu.org breezy/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://koti.mbnet.fi breezy/ Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Ign http://deb.opera.com etch/non-free Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://deb.opera.com etch/non-free Packages
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 258B in 14s (18B/s)
Reading package lists... Done
W: GPG error: http://koti.mbnet.fi breezy/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E8DDB29170188C3B
W: GPG error: http://kubuntu.org breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
isos@ubuntu:~$ sudo apt-get update Ign http://theli.free.fr ./ Release.gpg
Get:1 http://koti.mbnet.fi breezy/ Release.gpg [65B]
Ign http://wine.lowvoice.nl breezy Release.gpg
Get:2 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:4 http://kubuntu.org breezy Release.gpg [189B]
Hit http://wine.lowvoice.nl breezy Release
Ign http://theli.free.fr ./ Release
Hit http://koti.mbnet.fi breezy/ Release
Ign http://koti.mbnet.fi breezy/ Release
Hit http://security.ubuntu.com breezy-security Release
Ign http://wine.lowvoice.nl breezy/main Packages
Get:5 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Ign http://deb.opera.com etch Release.gpg
Ign http://theli.free.fr ./ Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Ign http://wine.lowvoice.nl breezy/main Sources
Ign http://koti.mbnet.fi breezy/ Packages
Get:6 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://wine.lowvoice.nl breezy/main Packages
Hit http://theli.free.fr ./ Packages
Hit http://kubuntu.org breezy Release
Ign http://kubuntu.org breezy Release
Hit http://archive.ubuntu.com breezy Release
Ign http://koti.mbnet.fi breezy/ Sources
Hit http://wine.lowvoice.nl breezy/main Sources
Hit http://archive.ubuntu.com breezy-updates Release
Ign http://deb.opera.com etch Release
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://koti.mbnet.fi breezy/ Packages
Hit http://archive.ubuntu.com breezy-backports Release
Hit http://kubuntu.org breezy/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://koti.mbnet.fi breezy/ Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Ign http://deb.opera.com etch/non-free Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://deb.opera.com etch/non-free Packages
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 258B in 14s (18B/s)
Reading package lists... Done
W: GPG error: http://koti.mbnet.fi breezy/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E8DDB29170188C3B
W: GPG error: http://kubuntu.org breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: You may want to run apt-get update to correct these problems


```

SAME ERROR. and what a suggestion: W: You may want to run apt-get update to correct these problems! same thing ...

---

### Post by sYs^ on 2006-05-05
You may use the original ubuntu sources.list.

```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

and check this thread:
[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by Isoss on 2006-05-05
Alright, it worked. but WHY there are so many suggestions concerning the repositoris? I mean, I have set the source.list to "enable extra repositories" ... isn't there some list that just enables everything with out errors?

Is there a list that I can stick to it? This is a very annoying thing in linux ... why do I always have to change the repositories?

---

### Post by sYs^ on 2006-05-05
I think you can stick to the default source.list and you won't have to change that file.
You may change it if you want add some 3rd party repos like really new unstable releases and stuff like that, mostly those are working too but for the most of them you will have to add a public key. But that will be quoted too.

---

### Post by Isoss on 2006-05-05
how can I add a public key?

---

### Post by sYs^ on 2006-05-06
```
# If you get errors about missing keys follow these command's :
# gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
# gpg --export --armor 33BAC1B3 | sudo apt-key add -
```

like this, but I don't know the details :>

---

### Post by Cobbs on 2007-09-04
thanks mate, that solved my problem!

---

