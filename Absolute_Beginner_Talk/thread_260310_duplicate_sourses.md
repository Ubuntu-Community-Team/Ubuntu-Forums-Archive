---
title: "duplicate sourses"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by dmichaels on 2006-09-18
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)


im new to ubuntu and linux. i keep getting this message. i would love to know how to rectify this dilema. thanks.

---

### Post by ewl1217 on 2006-09-18
You need to edit the file "/etc/apt/sources.list" (without the quotes). You can view and edit it with the command "gksudo gedit /etc/apt/sources.list" (again, without the quotes). Find the duplicate entry and remove it. If you're not sure what to do, just post the contents of the file here.

---

### Post by dmichaels on 2006-09-18
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

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
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
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
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted

---

### Post by dmichaels on 2006-09-18
this is what came up. im not sure i can make sense of it yet:confused:

---

### Post by Poeffie on 2006-09-18
Try replacing it with the following:

```
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

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
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
```

---

### Post by dmichaels on 2006-09-18
forgive me but could u explain how to replace it. im thinking i would select all delete and paste the new code, is that it or am i just not getting this?

---

### Post by jd65pl on 2006-09-18
Yes delete this information in /etc/apt/sources.list and replace it with one of the ones already posted.

Edited: Mistypes due to wireless keyboard running out of batteries!

---

### Post by dmichaels on 2006-09-18
thanks so much for your help. how do i check to make sure the problem is corrected?

---

### Post by Poeffie on 2006-09-18
retry the command you tried before:
"sudo apt-get update" in a terminal should do the trick

---

### Post by jd65pl on 2006-09-18
Type

```
sudo apt-get update
```

In the terminal if you get no error messages the list is fine.

J

---

### Post by dmichaels on 2006-09-18
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:5 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Fetched 76B in 5s (15B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
drew@reborn:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory



this is what came up

---

### Post by Poeffie on 2006-09-18
Perhaps you should try this: it disables your previous settings and uses the new ones:
```

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
#deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe

## Ubuntu Software
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
```
Now do:
```
sudo apt-get update
```

---

### Post by jd65pl on 2006-09-18
```

#
# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb http://de.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted
## or updates from the Ubuntu security team.
```

Try replacing the list with my sources list and then run

```
sudo apt-get update
```

---

### Post by dmichaels on 2006-09-18
thanks for the help. i just installed ubuntu last night after i got sick of windows. ive been trying to understand it ever since. time for more reading

---

### Post by dmichaels on 2006-09-18
i ran sudo apt-get update again this time no error messages 

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Fetched 6B in 1s (5B/s)
Reading package lists... Done


i hope this means that the issue is resolved?

---

### Post by jd65pl on 2006-09-18
Yes this is now resolved!

---

### Post by Poeffie on 2006-09-18
Yes, now everything should be fine. If you ever wish to add a new repository (probably not), then you should just add "deb http://<etc...>" to that file.

Have a great time exploring ubuntu :d

---

### Post by dmichaels on 2006-09-18
thanks so much again. :D now i must find out what a repository is..and if i need to use one.

---

### Post by Poeffie on 2006-09-18
What you used where the repositories. They are lists of programs you can download trough aptitude, synaptic or with the apt-get command.

Sometimes if you need to install a program and it is located in another repository then the ones you are using now (the three last lines in my post), then you just add it as I told.

There is also a way to do this graphically trough System -> Administration -> Software Properties

If you want to check if a file is available in the official repositories, then this is a useful link:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by jd65pl on 2006-09-18
You could have a look at this page on the ubuntu wiki...

[https://help.ubuntu.com/community/Repositories]("https://help.ubuntu.com/community/Repositories")

---

