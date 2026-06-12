---
title: "error in package manager"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by timofthec on 2006-07-21
I have updates waiting to be installed but when I try I get the message "Error opening the cache (E: Malformed line 34 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.)

I'm advised to use apt-get on a terminal to see whats wrong but when I use the command I simply get a desciption of what apt-get does with a list of options.

I also tried add/remove from applications and that gives me another error message - /home/chambos/Desktop/Screenshot.png
 (hope that works)

anybody got any ideas what I need to do to sort this out?

EDIT - ok the link didnt work so I've tried to add it as an attachment

---

### Post by ubuntu-geek on 2006-07-21
Try this solution and see if it helps. It sounds much like what you are having..

[http://ubuntuforums.org/showpost.php?p=1081442&postcount=9](http://ubuntuforums.org/showpost.php?p=1081442&postcount=9)

---

### Post by timofthec on 2006-07-21
OK I did a few of thinks listed ion the thread but none seemed to work and the others I didn't understand.

It certainly seems the same problem as listed in that thread but I think I need a simpler solution if one exists :(

---

### Post by timofthec on 2006-07-22
I'm still looking for help on this if anybodys got any ideas

---

### Post by SkyNet2029 on 2006-07-22
Could you post your /etc/apt/sources.list here. It just looks to have failed a Sanity (validity) test when it was read by your package manager. Meaning that there was probably a character where a space was expected, or vice-versa.

---

### Post by timofthec on 2006-07-22
Hi skynet, my sources.list is as follows:-


deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
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
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) 

Hope this means something to ya :D

---

### Post by SkyNet2029 on 2006-07-22
Ermm, as near as I can see:
Since I have no idea what was up above the rest of your sources.list, I had no idea where line 34 actually was. BUT,
it is listed as an (DIST), so basically the distribution is not understood by the package manager.
Please change this line:
```
deb http://wine.budgetdedicated.com/apt
```


To this:
```
deb http://wine.budgetdedicated.com/apt dapper main
```
to let package manager know what archive to access for wine.

then 
```
$sudo apt-get update
```

---

### Post by timofthec on 2006-07-22
hmm, ubuntu will not let me change the sources.list file.  It tells me that "You are not the owner, so you can't change these permissions"

I only have one account setup and I do not know how to change the permissions.  Do I need to be logged on as some form of administrator?  I've seen the term "super user" somewhere, is that what I need to be?

Sorry - more help neded so I can make use of the help already given:D

---

### Post by SkyNet2029 on 2006-07-22
sorry about that, try this, using Terminal :

```
$ sudo nano /etc/apt/sources.list
```

edit the content, then CTRL-X to save changes.

You do need to be SuperUser to do these (and most) changes in Linux. I get carried away sometimes, sorry.

---

### Post by timofthec on 2006-07-22
brilliant!!!

that got it Sky, many thanks for your help:D

---

### Post by SkyNet2029 on 2006-07-22
Coolness. Glad I could help.

---

