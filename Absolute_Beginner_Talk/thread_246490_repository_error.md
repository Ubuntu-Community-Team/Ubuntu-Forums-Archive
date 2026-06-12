---
title: "repository error"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by sailor2001 on 2006-08-29
E: Type 'sudo' is not known on line 37 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
  
tried to follow 2 different threads on installing windows ntfs and something happened.. I think those threads are 2 confusing   
synaptics doesn't work anymore

---

### Post by Bachstelze on 2006-08-29
Could you pleae paste your sources.list ?

---

### Post by sailor2001 on 2006-08-29
and herein is the problem;  /etc/apt/sources.list  gives me permission denied

---

### Post by sailor2001 on 2006-08-29
bump

---

### Post by calvinthomas on 2006-08-29
Go to a terminal and type sudo gedit /etc/apt/sources.list, then go down to line 37 (it'll tell you what line your on at the bottom) and delete it, that'll fix it, alternatively do above and post sources list here and someone might offer a better solution

Calv

---

### Post by Bachstelze on 2006-08-29
Please don't !!

Use gksudo instead of sudo !

**calvinthomas**, please have a look at [this](https://help.ubuntu.com/community/RootSudo).

> **NEVER** use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail.

---

### Post by sailor2001 on 2006-08-29
sailor@sailor-desktop:~$ sudo gedit/etc/apt/sourses.list
Password:
sudo: gedit/etc/apt/sourses.list: command not found
sailor@sailor-desktop:~$

---

### Post by calvinthomas on 2006-08-29
Yikes, thanks for the tip, i've never ever used it and never had any problems but I won't be risking it in the future, sorry to the original user for any problems I might have caused.

Calv

---

### Post by calvinthomas on 2006-08-29
> **sailor2001 said:**
> sailor@sailor-desktop:~$ sudo gedit/etc/apt/sourses.list
Password:
sudo: gedit/etc/apt/sourses.list: command not found
sailor@sailor-desktop:~$

Apologies, you need a space between gedit and /etc

Calv

---

### Post by sailor2001 on 2006-08-29
sailor@sailor-desktop:~$ gksudo gedit /etc/apt/sources.list

(gedit:5351): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
sailor@sailor-desktop:~$

---

### Post by calvinthomas on 2006-08-29
I've never seen that error before so i'm hoping someone else can help, just incase its a problem with gedit (Wild guess!) try this:

sudo nano /etc/apt/sources.list (Note sudo is correct I think in this case as nano runs from the terminal command line)

Calv

---

### Post by sailor2001 on 2006-08-29
GNU nano 1.3.10          File: /etc/apt/sources.list


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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiversedeb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
                               [ Read 40 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

---

### Post by dannyboy79 on 2006-08-29
Sailor2001, what has happened is that youhave accidentally messed up your sources.list. It is no big deal at all. What these other's are trying to do is help you figure out which line to delete but I believe it is easier than that! What you can do is first of all go to the line that has 2 repositories on 1 line and hit the enter key immediately after the word "multiverse" so that the following goes on it's own line "deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe". next since I don't believe you have posted your entire sources.list you need to scroll down it and find line number 37 or any line that begins with "sudo", you must have accidentally pasted "sudo" within the begining of one of your repository lines.Also I really hope that all tha garbage like "G Get Help O WriteOut R Read File blah blah blah that you have pasted in this thread isn't in your sources.list but it's merelry a screen shot somehow. If all that stuff is in there you either need to delete it all or if your not comfortable with what to delete, put "##" at the begining of each line that DOESN'T start with "deb". So that you can understand more, what your sources.list contains is basically all the website's that contain all the software that you can install into Ubuntu using aptitude or apt-get and since you have garbage or lines that apt-get doesn't understand how to read since it's not in a format like "deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe" your synaptics program is going to fail because it's trying to update your synaptics list with all the software that's normally available for Ubuntu. If you don't get it resolved, send me a PM and I'll send you a copy of my sources.list to an email address for ya. This is no bug deal, don't sweat it, you'll be back up in no time!

---

### Post by Bachstelze on 2006-08-29
sailor2001, the message you got when running gksudo gedit /etc/apt/sources.list is normal. Gedit should have opened nonetheless with your file in it, please copy/paste it here :)

---

### Post by sailor2001 on 2006-08-29
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
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) dapper main
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) dapper main
sudo apt-get update
sudo apt-get upgrade


hey!!!!!!!!!11 it works now..... thanks guys, you made my day

---

