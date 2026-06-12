---
title: "Ubuntu gnome-RDP Installation"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by cnsrvative on 2007-03-23
Trying to install gnome-RDP for Ubuntu (DD).  Newbie [conforming MS guy - so be gentle... :) ]

Trying to install gnome-RDP (source:[http://sourceforge.net/project/showfiles.php?group_id=158223](http://sourceforge.net/project/showfiles.php?group_id=158223))

Followed instructions for adding source to sources.list and using installation commands per instructions at: [http://gnome-rdp.linuxforge.hu/?q=node/7](http://gnome-rdp.linuxforge.hu/?q=node/7)

Results (running as root):

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-rdp: Depends: libglade2.0-cil (< 2.5.0) but 2.8.2-0ubuntu5 is to be inst alled
             Depends: libglib2.0-cil (< 2.5.0) but 2.8.2-0ubuntu5 is to be insta lled
             Depends: libgtk2.0-cil (< 2.5.0) but 2.8.2-0ubuntu5 is to be instal led
             Depends: libvte2.0-cil (>= 2.3.90) but it is not installable
             Depends: libvte2.0-cil (< 2.5.0) but it is not installable

contents of sources.list.d

# 
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://phanatic.hu/debs](http://phanatic.hu/debs) ./

deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by charles.g.moore on 2007-03-23
I think you should uncomment all of the lines beginning with deb in your sources.list
do a sudo aptitude update
       sudo aptitude upgrade
       sudo aptitude install gnome-rdp
I believe I grabbed it off the repo's when I installed it

---

### Post by AndrewBarber on 2007-03-23
Just checked and gnome-rdp is in the unviterse repo.
As charles.g.moore advised,
Uncomment all the line in your /etc/apt/sources.list that have one # before them. 
then do the commands he has said.

---

