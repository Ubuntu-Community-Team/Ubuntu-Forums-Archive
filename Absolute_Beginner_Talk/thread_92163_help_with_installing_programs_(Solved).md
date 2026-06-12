---
title: "help with installing programs (Solved)"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by aznboi on 2005-11-18
This is really annoying.... I am so used to those installers for windows i really need help with this... I am trying to install totem, the media player and i do
```
./configure
```
and i get an error:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for g++... g++
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.

```

how do i fix this? thnx for the help!

---

### Post by adwait on 2005-11-18
I think that would be
```
sudo apt-get install build-essentials
```

---

### Post by aznboi on 2005-11-18
thnx will try that,

---

### Post by andlinux21 on 2005-11-18
i dont think you have to ./connfigure anymore with ubuntu most stuff will install with 

sudo apt-get install <package>

as long as your repositories are set right :razz:

---

### Post by aznboi on 2005-11-18
so can i just cd to my folder with the files and do apt-get install filename?

wat is a repository?

thnx alot

---

### Post by TypesWithFist on 2005-11-18
[FONT="Comic Sans MS"][/FONT]
Great!!  That was my biggest problem, how to install programs.  I'm trying that with Nero for Linux tonight.  Thanks  (I'm learning this on an extra computer.  My little Duron workhorse....)

---

### Post by Vorian on 2005-11-18
[QUOTE=aznboi]so can i just cd to my folder with the files and do apt-get install filename?

wat is a repository?

thnx alot[/QUOTE]

Listed in /etc/apt/sources.list (sudo gedit /etc/apt/sources.list)

```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
#deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
#deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
#deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
#deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

That is what you should have at a minimum.

---

### Post by Vorian on 2005-11-18
[QUOTE=TypesWithFist][FONT="Comic Sans MS"][/FONT]
Great!!  That was my biggest problem, how to install programs.  I'm trying that with Nero for Linux tonight.  Thanks  (I'm learning this on an extra computer.  My little Duron workhorse....)[/QUOTE]

You'll have to use dpkg, apt-get will not work for nero.  

Have you tried gnomebaker?  (sudo apt-get install gnomebaker?)

---

### Post by aysiu on 2005-11-19
[The different ways to install software in Ubuntu](http://www.psychocats.net/linux/installingsoftware.php)

By the way, I nominate K3B, even for Gnome. Though Gnomebaker and Graveman aren't too bad either.

---

### Post by Vorian on 2005-11-19
[QUOTE=aysiu][The different ways to install software in Ubuntu](http://www.psychocats.net/linux/installingsoftware.php)

By the way, I nominate K3B, even for Gnome. Though Gnomebaker and Graveman aren't too bad either.[/QUOTE]

K3B is hard to beat!

---

### Post by aznboi on 2005-11-19
thnx for the help. I found the Add Applications under the Applications menu and it is soo easy to use. Thnx

---

### Post by Vorian on 2005-11-19
[QUOTE=aznboi]thnx for the help. I found the Add Applications under the Applications menu and it is soo easy to use. Thnx[/QUOTE]

That's the way:)

---

