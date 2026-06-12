---
title: "package installer is saying dependency is not satisfiable but i have it installed"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by kaboom on 2007-03-12
hey all
i'm trying to install libakamaru0 because apparently its a good time and eventually i'll need it for kiba dock.  i hit a problem when i try to open the .deb file from this site: [http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/dists/edgy/beryl-svn/)

in package installer it says "error: dependency not satisfiable: libc6
my first thought was 'sudo apt-get install libc6'   the output for that is what confused me:  
> kaboom@kaboom-laptop:~$ sudo apt-get install libc6
Password:
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

so if its allready the newest version how is it an unmet dependency?]
i'm in dapper by the way.
thanks for looking 
chris

---

### Post by chuckyp on 2007-03-13
Its possible that the deb you are trying to install requires a different version of libc6.  Always be careful installing debs that aren't in the repositories for reasons like this.  You may want to check Administration > Synaptic  and see if kiba dock is in the repos.  If so just install from there this will take care of all your dependency problems.

---

### Post by kaboom on 2007-03-13
hey thanks for the reply.  when i tried to install it in synaptic i got the same kind of message:
kiba-dock:
 Depends: libakamaru0 but it is not going to be installed
  Depends: libatk1.0-0 (>=1.12.1) but 1.11.4-0ubuntu1 is to be installed
  Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
  Depends: libcairo2 (>=1.2.4) but 1.0.4-0ubuntu1 is to be installed
  Depends: libglib2.0-0 (>=2.12.0) but 2.10.3-0ubuntu1 is to be installed
  Depends: libgtk2.0-0 (>=2.10.3) but 2.8.20-0ubuntu1.1 is to be installed
  Depends: libpango1.0-0 (>=1.14.5) but 1.12.3-0ubuntu3 is to be installed
 Depends: kiba-plugins but it is not going to be installed
 Depends: gset-kiba but it is not going to be installed

d  Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
  Depends: libcairo2 (>=1.2.4) but 1.0.4-0ubuntu1 is to be installed
  Depends: libglib2.0-0 (>=2.12.0) but 2.10.3-0ubuntu1 is to be installed
  Depends: libgtk2.0-0 (>=2.10.3) but 2.8.20-0ubuntu1.1 is to be installed
  Depends: libpango1.0-0 (>=1.14.5) but 1.12.3-0ubuntu3 is to be installed
 Depends: kiba-plugins but it is not going to be installed
 Depends: gset-kiba but it is not going to be installed

here are the repos in my /etc/apt/sources.list:
## beryl stuff
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main
deb-src [http://ubeb](http://ubeb) [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main


##mplayer source
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

##kiba jenk
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

##check gmail repos
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper main dupdate french

deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://kubuntu.org/packages/amarok-143](http://kubuntu.org/packages/amarok-143) dapper main
deb [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) experimental/
deb-src [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) experimental/
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main

is there anything someone notices that might be causing the problem?
thanks 
c

---

### Post by compmodder26 on 2007-03-13
It looks to me like that .deb was created for a version of ubuntu higher than dapper (either edgy or feisty).  The versions of the libraries it requires are higher than ones in the dapper repositories.

---

### Post by kaboom on 2007-03-13
ok sounds good thanks for the help i'll look for another .deb

---

### Post by max_power on 2007-03-13
You could try to build it from source as a last resort...:guitar:

---

### Post by dannyboy79 on 2007-03-13
yeah, you can't just add another version of ubuntu to your source.list and install software from it, this is a great way to break your entire install. this would be like trying to install norton ghost 9.0 onto win98se, it just can't be done, you need to install the 2003 version. so this is the case with this. otherwise you'll have to backport it yourself and there is a tutorial for this. heres the link: [http://ubuntuforums.org/showthread.php?t=268687](http://ubuntuforums.org/showthread.php?t=268687)

---

### Post by compmodder26 on 2007-03-13
On further review of your sources.list, I noticed that you have a few edgy repositories in there as well.  This is a good way to break your system.  Be very careful with that.

---

### Post by taurus on 2007-03-13
Yes, your system will be "kaboom" soon if you continue using that /etc/apt/sources.list.  Should remove the edgy repos while you still have a chance.

---

### Post by kaboom on 2007-03-13
ok thanks for the heads up on that.

---

