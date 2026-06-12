---
title: "Error message &quot;Duplicate sources...&quot;"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by andrew.46 on 2007-01-22
Hi,

 When checking for system updates I get a message that says:

> W: Duplicate sources.list entry [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_dapper_main_binary-i386_Packages)

  Now I have tracked down /var/lib/apt/lists and I can see only one entry for [www.getautomatix.com_apt_dists_dapper_main_binary-i386_Packages](www.getautomatix.com_apt_dists_dapper_main_binary-i386_Packages) although in a folder marked 'partial' there is an intriguing file called: [www.getautomatix.com_apt_dists_dapper_main_binary-i386_Packages.decomp](www.getautomatix.com_apt_dists_dapper_main_binary-i386_Packages.decomp)

  I thought that this might be the problem (I installed Automatix 2ce through stupidity) and attempted to delete the 'partial' folder and contents. However I cannot delete this: delete is greyed out.

 Any thoughts / suggestions?

                     Andrew

---

### Post by jordanmthomas on 2007-01-22
Can you post the output of 
```
cat /etc/apt/sources.list
```

It looks like your automatix entry is in there twice.

---

### Post by andrew.46 on 2007-01-22
Hi Jordanmthomas,

 Thanks for our reply:

> **jordanmthomas said:**
> Can you post the output of 
```
cat /etc/apt/sources.list
```

It looks like your automatix entry is in there twice.

 my /etc/apt/sources.list is:


```
deb http://au.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
# deb cdrom:[Xubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb http://www.getautomatix.com/apt dapper main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper multiverse
#AUTOMATIX REPOS END
deb http://www.getautomatix.com/apt dapper main

```

 Not sure what I can / should edit out of this?

                      Andrew

---

### Post by jordanmthomas on 2007-01-22
Find one of these lines (you do have two)
```
deb http://www.getautomatix.com/apt dapper main
```
and either delete it or put a # in front of it

(in case you don't know how to edit it)
```
gksudo gedit /etc/apt/sources.list
```
Then, in a terminal, 
```
sudo apt-get update
```

---

### Post by andrew.46 on 2007-01-22
Hi jordanmthomas,

 Thank you very much for that: all is now well! I substituted mousepad for gedit (as I am running Xubuntu, is gedit the default text editor for Ubuntu/Gnome?)

  I am familiar with sudo, can I ask what gksudo adds to the command? I found:

> You are supposed to use one of these two commands when you need root access. sudo is for when you are in the terminal and need root access and gksudo is when you are in the GUI and need root access, for example you can press alt+f2 and type "gksudo appname".

 but I can't quite get my head around it, I used a terminal for both commands with no problem, was this incorrect?

  Thanks for your trouble,

             Andrew

---

### Post by randiroo76073 on 2007-01-22
sudo is for command line applications & gksudo is for GUI based applications. Altho sudo will work for both, I don't think gksudo will work for straight command line applications.  Hope this helps :)

---

### Post by ubuntosh on 2007-01-24
im having the same problem but i couldn't get to edit /var/lib/apt/lists. how can i do that?
thnx a lot:)

---

### Post by jordanmthomas on 2007-01-24
You need to edit /etc/apt/sources.list, not /var/lib/apt/lists
```
gksudo gedit /etc/apt/sources.list
```

---

