---
title: "Problems with add/remove, Synaptic and apt-get.."
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by urk_nono on 2006-11-30
Okay, I am extremely new to Linux and Ubuntu, please have patience with me.

I was browsing the forums to find a way to install an IRC client, and found out that xchat is something ubuntu has. I think I entered a command in terminal, but to be frank I can't remember what I jotted in. So then I found out that I just had to add it by entering either Synaptic or Add/remove. Then I tried:

**Opening Synaptic...**
E: Malformed line 2 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

**Opening Add/remove..**
Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

**In terminal..**
/etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied

*I have absolutely no clue why I get permission denied. I tried to enter root and do it, but then this happened: *

sudo apt-get update
E: Malformed line 2 in source list /etc/apt/sources.list (URI parse)

I feel screwed. Anyone got a helping hand available? 

:confused:

---

### Post by urk_nono on 2006-11-30
Tried installing xchat via Automatix2, then I got this: 

FATAL ERROR: Xchat
An apt-based error occured and installation was unsuccessful

Seems to me that the problem is linked to eachother, though I'm a newbie and generally have no clue...

Edit:
I tried reading this [thread]("http://ubuntuforums.org/showthread.php?t=254301&highlight=major+failure") But I didn't understand..

---

### Post by kylevan on 2006-11-30
ok... open a terminal and type:

```
sudo gedit /etc/apt/sources.list
```

when gedit loads up, find the second line of the file and delete it. save the file and close gedit.

in the terminal, type:

```
sudo apt-get update
```

let us know if that works.  from the error messages, it sounds like you mis-typed something when adding a repository to the list that APT checks.

---

### Post by urk_nono on 2006-12-01
deb None edgy main restricted
[COLOR="Red"]deb-src None edgy main restricted[/COLOR]

## Major bug fix updates produced after the final release of the
## distribution.
deb None edgy-updates main restricted
deb-src None edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
  

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb None edgy-backports main restricted universe multiverse

deb None edgy-updates main restricted universe multiverse

deb None edgy-security main restricted universe multiverse

deb None edgy main restricted universe multiverse
#AUTOMATIX REPOS END

I tried deleting the line wich was all the way on top marked in red, but I guess that wasn't right :-|

---

### Post by konst88 on 2006-12-01
All the lines with the word None seems to me incorrect.
You may comment them by adding # to the beginning of the line.

---

### Post by urk_nono on 2006-12-02
Scratch that, Konst88 - you the man!

---

### Post by lamego on 2006-12-02
1) Open a terminal
2) Type: 
```
sudo gedit /etc/apt/sources.list
```

Delete all the contents and copy paste the following default sources.list:
```
deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

```
3) Type:
```
sudo apt-get update
```
4) Do not type commands and do not edit configurations files unless you understand what you are doing otherwise you will be breaking your system.

---

