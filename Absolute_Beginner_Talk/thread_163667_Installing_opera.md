---
title: "Installing opera?"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by azmansell on 2006-04-21
Hi there,
I have tried many times to install opera and just cant get it to work!

i have followed lots of different tutorials but all i get is dependency errors. 

can any one help?

---

### Post by gingermark on 2006-04-21
This method works great: [https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)
You could work through it, and post if you have any problems.

---

### Post by Sef on 2006-04-21
What dependency errors are you getting?  You will need to download the dependencies to make it install.

If you do the sudo dkpg -i option and you get dependency errors, do this

sudo apt-get -f install

[https://wiki.ubuntu.com/OperaBrowser?highlight=%28opera%29]("https://wiki.ubuntu.com/OperaBrowser?highlight=%28opera%29")

---

### Post by azmansell on 2006-04-21
heres what comes up when i try that tutorial....

azmansell1@ubuntu:~/Desktop$ sudo dpkg -i opera_9.0-20060411.6-shared-qt_en_etch _i386.deb
Selecting previously deselected package opera.
(Reading database ... 60850 files and directories currently installed.)
Unpacking opera (from opera_9.0-20060411.6-shared-qt_en_etch_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3-mt (>= 3.3.4); however:
  Package libqt3-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera
azmansell1@ubuntu:~/Desktop$


and heres what i get when i try the next tip (sudo apt-get -f install)


azmansell1@ubuntu:~/Desktop$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  opera
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 12.5MB disk space will be freed.
Do you want to continue [Y/n]?


if i hit y, it just deletes opera and im back to square one?

---

### Post by gingermark on 2006-04-21
Which version of Ubuntu are you using? (ie Hoary, Breezy etc,) Also, please could you post the contents of your sources.list file located in /etc/apt.

I am running Opera 9 beta at the moment, and I have the library happily installed, so it sounds like a repository problem.

---

### Post by azmansell on 2006-04-21
im pretty sure its breezy. i downloaded it from the ubuntu website last week (although how do i check which version i have)

the contents of my sources.list file are....

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

-------------------------------------------------------------
cheers for your help by the way!

---

### Post by gingermark on 2006-04-21
Yeah, ok you need to edit this file and remove the '#' symbols in front of the lines that begin 'deb', and save the file. Each line that begins 'deb' is a repository of software available to you, and the '#' symbols block them.

Then type 'sudo apt-get update' and try again.

---

### Post by azmansell on 2006-04-21
cheers, ill try that!

---

### Post by azmansell on 2006-04-21
FANTASTIC!! you are an absolute superstar - cheers!!!

:KS :KS :KS

---

### Post by gingermark on 2006-04-21
Glad it worked.

---

### Post by gardara on 2006-04-21
Has anyone got opera 9 beta working on dapper? I downloaded and installed a breezy version of opera 9b (as they dont have a dapper version) and it did install but it won't open ](*,)  
Anyone having any luck with it?

---

### Post by gingermark on 2006-04-21
[QUOTE=gardara]Has anyone got opera 9 beta working on dapper? I downloaded and installed a breezy version of opera 9b (as they dont have a dapper version) and it did install but it won't open ](*,)  
Anyone having any luck with it?[/QUOTE]
Have you tried installing any of the Debian debs? Hasn't Dapper been synced with the unstable branch relatively recently?

---

### Post by gardara on 2006-04-21
I haven't tried any debian deb's. Which one debian deb should I try? 
Debian Unstable (Sid)
Debian Testing (Etch)
Debian 3.1 (Sarge)
Debian 3.0 (Woody)
Debian 2.2 (Potato)

---

### Post by gingermark on 2006-04-21
I'd give the Unstable & Testing ones a go, and see if they work. I'm just guessing, but I've give the Testing one a go first.
EDIT: Or maybe the unstable one, as that's the branch Ubuntu syncs to. It's fairly obvious I'm not 100% on whether this will work, but I'd be interested to know the results :)

---

