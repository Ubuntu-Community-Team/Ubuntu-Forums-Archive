---
title: "Error Msg in Synaptic Manager and apt-get"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by goyan on 2005-11-04
Every time I open the Synaptic Manager or use the apt-get command, I get this error msg, and it starts to get annoying:

```

W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://gb.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

```

My sources.list files looks like this:
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

```

Thank you for your time.

Goyan

---

### Post by matthewv on 2005-11-04
try ```
sudo apt-get update
```

---

### Post by mlomker on 2005-11-04
There aren't any backports yet because Breezy is still too new to be backporting packages from Drake.  You can # those out in your sources.list file for now.

---

### Post by nrwilk on 2005-11-04
I was getting the same thing until I commented out these two repositories:
```
deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

I think this has to do with the fact that Breezy is new and has no backports available.

I could be completely wrong, but after commenting those repositories out, the errors went away.

EDIT: whoops, you beat me to it. hehe

---

### Post by goyan on 2005-11-04
Graet!!! No more error msgs. Btw, when will the Breezy start to have backport repositories then? I am quite to all these Linux stuff, not really sure about "universe, multiverse and backport system".

---

### Post by nrwilk on 2005-11-10
[QUOTE=goyan]when will the Breezy start to have backport repositories then?[/QUOTE]

NOW!
[http://fridge.ubuntu.com/node/137](http://fridge.ubuntu.com/node/137)

---

### Post by Darrin on 2005-11-10
[QUOTE=Fealos]NOW!
[http://fridge.ubuntu.com/node/137](http://fridge.ubuntu.com/node/137)[/QUOTE]

How do I get the backports. The ones I have dont seem to work. I get errors when checked.

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://us.archive.ubuntu.com/ubuntu/ breezy multiverse universe main restricted
```

---

### Post by nrwilk on 2005-11-10
[QUOTE=Darrin]How do I get the backports. The ones I have dont seem to work. I get errors when checked.

```
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```[/QUOTE]

Try them again, the Breezy backports have only JUST been enabled today.  Those look correct, the addresses match mine.  I just uncommented them to try it and I'm not getting any errors.

Try this:
```
$ sudo apt-get update
```

---

### Post by Darrin on 2005-11-10
Still getting errors. When doing apt update heres what I get. I only posted starting with the first error on.

```
Err http://us.archive.ubuntu.com breezy-backports/main Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/restricted Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/universe Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/multiverse Packages
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/main Sources
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/restricted Sources
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/universe Sources
  404 Not Found
Err http://us.archive.ubuntu.com breezy-backports/multiverse Sources
  404 Not Found
Fetched 19.8kB in 9s (2094B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Darrin on 2005-11-10
Problem resolved. [I was reading this]("http://ubuntuforums.org/showthread.php?p=482249#post482249"). Basically I had to remove the "us" in front of the backport repo address.

---

### Post by nrwilk on 2005-11-10
[QUOTE=Darrin]Problem resolved. [I was reading this]("http://ubuntuforums.org/showthread.php?p=482249#post482249"). Basically I had to remove the "us" in front of the backport repo address.[/QUOTE]
crap, that's my fault.  Sorry, I missed that when comparing.

---

### Post by Darrin on 2005-11-11
[QUOTE=Fealos]crap, that's my fault.  Sorry, I missed that when comparing.[/QUOTE]
No worries. Im just happy its working now. :)

---

### Post by gurumac on 2006-04-06
[QUOTE=Darrin]Problem resolved. [I was reading this]("http://ubuntuforums.org/showthread.php?p=482249#post482249"). Basically I had to remove the "us" in front of the backport repo address.[/QUOTE]
Greetings fellow ubuntu user!

How do I get to this source file to edit it?

What are the commands for the terminal window?


Regards,

---

