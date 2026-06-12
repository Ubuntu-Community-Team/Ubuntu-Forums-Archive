---
title: "sudo apt-get update error"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-26
i am using lan cable.following error message was encoutered by my sudo apt-get update command

ejaz@ejaz:~$ sudo apt-get update
Password:
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages [3830B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
Fetched 2387B in 10s (222B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
ejaz@ejaz:~$

plz tell me about this.
is it proxy server failure or something else

---

### Post by carlosqueso on 2006-05-26
it looks like you may have a duplicate in your sources.list file....type sudo gedit /etc/apt/sources.list into a terminal and look for a duplicate.  If you can't, poste it here and I'll take a look at it myself.

---

### Post by u04f061 on 2006-05-26
[QUOTE=carlosqueso]it looks like you may have a duplicate in your sources.list file....type sudo gedit /etc/apt/sources.list into a terminal and look for a duplicate.  If you can't, poste it here and I'll take a look at it myself.[/QUOTE]

this is my file 

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe

---

### Post by carlosqueso on 2006-05-26
comment out (put two #'s in front of) the bottom line.  then when you use sudo apt-get update, it should work.

---

### Post by u04f061 on 2006-05-26
[QUOTE=carlosqueso]comment out (put two #'s in front of) the bottom line.  then when you use sudo apt-get update, it should work.[/QUOTE]
ok this has fixed my problem but can u tell me what the reason was.
i matched this with other but it was not matchin
it did'nt seem duplicate

---

### Post by Koech on 2006-05-26
The problem you mean is exactlywhat? The duplication in itself or the reason it couldn't update? Probably someone or you tried editing sources.list before, that's why it's always good to back up.

---

### Post by NeoGreen on 2006-05-26
Did you mean like this:
**##deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe**
or like this:
[B]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe
##[/B]

Sorry for jumping into the thread, but I was just curious about the problem.:)

---

### Post by Koech on 2006-05-26
Like this:
##deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe.
That's how you prevent the compiler from reading a line of code.

---

### Post by catlett on 2006-05-26
FYIA 
A # comments a line (i.e. makes the text ignored by the computer) because the computer takes the # to mean that text is a comment. If you remove a # then you uncomment the line of text and the computer will recognise it as information it should be using.

This is just to distinguish text that contains parameters or code for an aplication from an actual  comment put in to clarify something.
For example this 
> ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
is a comment about this repository>  deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse

 With repositories they will put a # (comment mark) in front of a url so that synaptic won't use it. They then put a comment in about the url and instructions to uncomment the line if you want it.

With repositories there are issues of applications not being updating from certain servers and some servers have non-free applications that are legal in some places of the world but illegal to instal in other places.
So they will ship with the repositories commented out with an explanation about the repo and a phrase telling you to uncomment the URL if you want apps from that server

---

### Post by Mustard on 2006-05-26
[QUOTE=u04f061]ok this has fixed my problem but can u tell me what the reason was.
i matched this with other but it was not matchin
it did'nt seem duplicate[/QUOTE]

It may not look like a duplicate, as in it doesnt look **exactly** like any other line, but the place it is accessing is a duplication of a previous instruction in that list to access the universe repository.

In this line instructions have been given to access all these repositories in one single line..

```
deb http://us.archive.ubuntu.com/ubuntu breezy **universe** multiverse
```

Then at the bottom you are attempting to access the universe repository listed in the above line again...

```
deb http://us.archive.ubuntu.com/ubuntu/ breezy **universe**
```

Note that both lines start with the same general location they are accessing..

```
deb http://us.archive.ubuntu.com/ubuntu/ breezy......
```

---

