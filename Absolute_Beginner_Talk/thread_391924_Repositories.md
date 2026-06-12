---
title: "Repositories"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by joel1a on 2007-03-23
OK  Help!!

In a Quest to open some repositories,  I screwed some things up I think, bad.  When I try to reload Synaptic Package Manager I get this Error  

E: Type 'http://archive.ubuntu.com/ubuntu' is not known on line 46 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: Type 'http://archive.ubuntu.com/ubuntu' is not known on line 46 in source list /etc/apt/sources.list
E: Unable to lock the list directory

I believe I cut and pasted a link and added to the list of Repositories.  What are my options?  Can I do some sort of factory default?

---

### Post by taurus on 2007-03-23
You can open a terminal, Applications -> Accessories -> Terminal, and edit your /etc/apt/sources.list with

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of line 46 to comment it out.  Save it and then run these two commands from a terminal again.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Hendrixski on 2007-03-23
I'm sure there's some easier way to do it from synaptic itself, but we're mostly nerds here, so yeah,  go to the line that's causing the error and just put a # at the begining to comment it out and it won't bother you again.

---

### Post by joel1a on 2007-03-23
This is what I got:

joel@joel-desktop:~$ gksudo gedit /etc/apt/sources.list

(gedit:7178): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Then this Source.list opened up:



## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

#AUTOMATIX REPOS END
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security multiverse universe main restricted

[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted

---

### Post by taurus on 2007-03-23
Remove this line (second from last) 

```
http://archive.ubuntu.com/ubuntu
```
and place a # in front of the last line unless you want to use the CD.  

Also, you need to replace this line

```
deb http://www.getautomatix.com/apt edgy main
```
with this one because you are running **dapper**, _not_ **edgy** (or remove it since you already have one further down).

```
deb http://www.getautomatix.com/apt dapper main
```
Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by joel1a on 2007-03-23
:)   Cool Back to Square One again Thanks!!    And I am a want to be geek...  Know enough to know that I don't know enough!:popcorn:

---

