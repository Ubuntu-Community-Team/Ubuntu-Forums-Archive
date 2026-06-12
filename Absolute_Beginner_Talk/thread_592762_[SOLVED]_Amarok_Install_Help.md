---
title: "[SOLVED] Amarok Install Help"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by LostLake on 2007-10-26
I tried installing amarok and this is what happens...

seth@seth-desktop:~$ sudo apt-get install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amarok

Any help will be greatly appreciated.

---

### Post by MegaJim on 2007-10-26
can you show us the output from

```
cat /etc/apt/sources.list
```

thanks

---

### Post by LostLake on 2007-10-26
seth@seth-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main

---

### Post by MegaJim on 2007-10-26
All of your repositories have been commented out automatically by aptitude!

Not seen this before!

You could try uncommenting (removing the # symbol) from any line that starts with "deb" and executing

```
sudo apt-get update
```

Could somebody who knows about aptitude authentication have a look at this please.

---

### Post by LostLake on 2007-10-26
I also tried to install amarok from the add/remove program and it tells me i cannot install because im using i386.

---

### Post by forestpixie on 2007-10-26
it might have had something to do with an upgrade, sure I read similar - I think if you're not connected it comments things out - I know for a fact it commented out medibuntu when I did mine.

Could always get a new one from source.o.matic - cracking name :)  [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by MegaJim on 2007-10-26
Oh, you could also try replacing the whole thing using the sources generator:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

edit: beaten!

---

### Post by Maestro23 on 2007-10-26
> **MegaJim said:**
> Oh, you could also try replacing the whole thing using the sources generator:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

edit: beaten!

Yeah, I would just use that.  Seems that upgrade is a pain for some.  I've seen too many threads with these source.list commented completely out.

---

### Post by forestpixie on 2007-10-26
> I've seen too many threads with these source.list commented completely out.

there seem to be a bunch of medibuntu ones afloat lately as well

---

### Post by LostLake on 2007-10-26
Sorry, but Im a noob. How do I use the source generator?

---

### Post by MegaJim on 2007-10-26
Click the link, choose your location

choose your distro (Gutsy)

choose your architecture

leave sources unchecked

click send

check the default repositories on the next page

click create sources.list

copy everything in that page

open up the sources.list

```
sudo gedit /etc/apt/sources.list
```

edit -> select all -> paste -> file -> save

close gedit

now you need to authenticate the source, in the terminal put

```
gpg --keyserver subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add -
```

replacing KEY with the key for each different gpg key in sources.list, then update sources

```
sudo apt-get update
```

now try getting amarok again.

---

### Post by forestpixie on 2007-10-26
and when all is installed - if you try to play an mp3 and gives you a big no no, you'll need this probably, although supposedly it'll do it for you - never did for me :(
so if it doesn't work try this in a terminal

```
sudo apt-get install libxine1-ffmpeg
```

---

### Post by LostLake on 2007-10-26
Wow! It worked, Thanks for the help! I dont know if I would have figured that out on my own...

---

### Post by Incense on 2007-10-26
> **forestpixie said:**
> and when all is installed - if you try to play an mp3 and gives you a big no no, you'll need this probably, although supposedly it'll do it for you - never did for me :(
so if it doesn't work try this in a terminal

```
sudo apt-get install libxine1-ffmpeg
```

The Mp3 bug was fixed (for me at least) with gutsy.

---

