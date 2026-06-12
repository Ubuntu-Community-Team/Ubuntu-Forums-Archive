---
title: "Installing other apps"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by kolakube on 2007-01-04
Hi there.

I have downloaded Amsn and a mac OS type theme.

Both of the install programs involves me extracting many files to to many different folders on the hard drive.  Its a time consuming process.

isn't there an app like an installer such as XP installer.  IE a GUI few clicks and its done?

Surely im doing this the hard way

Kola

---

### Post by Bachstelze on 2007-01-04
Everything you need to know about installing stuff is [here](http://www.psychocats.net/ubuntu/installingsoftware) :)

---

### Post by taurus on 2007-01-04
Theme:  System -> Preferences -> Theme -> Install Theme... And browse to where you have downloaded the theme!

Amsn:  Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install amsn
```

---

### Post by kolakube on 2007-01-04
Hi there,

tried to install from theme, got the jist of it but it says file format unrecognized.  any ideas?

Tried above re Amsn.  update works fine but install states no package of that name exists yet its right there on my desktop

---

### Post by taurus on 2007-01-04
What's the exact name of the theme and where did you download it?  Remember, you are not supposed to unpack it right after you download it.  The theme installer knows how to handle the .tar.gz format.

And for amsn, did you enable both universe and multiverse in /etc/apt/sources.list?  Paste your /etc/apt/sources.list here.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by livingtarget on 2007-01-04
Also if I remember correctly you may be able to install the theme by 'dragging-and-dropping' the tar.gz file in the theme window. :-k

---

### Post by kolakube on 2007-01-04
And for amsn, did you enable both universe and multiverse in /etc/apt/sources.list? Paste your /etc/apt/sources.list here.

Applications -> Accessories -> Terminal
Code:

cat /etc/apt/sources.list


^^^^^^^^^^

it says Bash, no such file or directory



Ive give up on the theme for now.  1 thing at a time :rolleyes:

---

### Post by meng on 2007-01-04
Are you sure you typed the command correctly?

---

### Post by ragnar_123 on 2007-01-04
> **livingtarget said:**
> Also if I remember correctly you may be able to install the theme by 'dragging-and-dropping' the tar.gz file in the theme window. :-k

...you surely remember correctly :-)

---

### Post by kolakube on 2007-01-04
Sry I must of typed it wrong.

Ive cut and paste now and get a huge load of text about 2 x a4.   want me to cut and paste it?

---

### Post by taurus on 2007-01-04
> **kolakube said:**
> Sry I must of typed it wrong.

Ive cut and paste now and get a huge load of text about 2 x a4.   want me to cut and paste it?

Yes, the complete /etc/apt/sources.list.

---

### Post by kolakube on 2007-01-04
oem@ubuntu:~$ cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
oem@ubuntu:~$

---

### Post by taurus on 2007-01-04
Okay, here is your new /etc/apt/sources.list.  You can edit it with 

Applications -> Accessories -> Terminal
```
gksudo gedit
```

```

#
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

#deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```
Save it and then run

```
sudo aptitude update
sudo aptitude install amsn
```

---

### Post by kolakube on 2007-01-04
Thnx m8

Wen you say the above you say save it.  what do I call it and where do I put it?

if i just call it 'code' and save it without changing anything I get the following message after typing the bottom two lines you specify

Fetched 3B in 0s (4B/s)
Reading package lists... Done
oem@ubuntu:~$ sudo aptitude install amsn
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "amsn"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
oem@ubuntu:~$

---

### Post by meng on 2007-01-04
gksudo gedit /etc/apt/sources.list

Then replace old text with taurus' text.
Then save.

Then:
sudo aptitude update
sudo aptitude install amsn

---

### Post by kolakube on 2007-01-04
sry meng i dont get ya.

what is  	gksudo gedit /etc/apt/sources.list

is this something i write into terminal?

if so this is what i did but had no idea where to save it too so instead of replacing its probs saved at a diff location

---

### Post by sailor2001 on 2007-01-04
when you close off your list, it will pop-up a screen to ask you if you want it saved

---

### Post by kolakube on 2007-01-04
and then it asks what i want to call it

IE save as  - unsaved document.

Unless I call it the same name as the file im replacing wont it just save as a seperate file and not replace anything??

---

### Post by taurus on 2007-01-04
If you look at my version and your version of /etc/apt/sources.list, you would see that I placed a # in front of the second line (of text) and removed the # in front of the rest of "**deb**".  Therefore, edit /etc/apt/sources.list and try to make yours to look like my version...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Then, save it and run those two commands to install amsn...

```
sudo aptitude update
sudo aptitude install amsn
```

---

