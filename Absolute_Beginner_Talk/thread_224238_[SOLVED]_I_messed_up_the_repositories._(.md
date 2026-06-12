---
title: "[SOLVED] I messed up the repositories. :("
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by RonB123123 on 2006-07-27
I messed up the repositories and is there any way I can make it go to the default settings? All the indexes are gone and I keep getting this error because I added a deb and I don't know how to remove it. This is the error.

E: Type 'http://wine.budgetdedicated.com/apt' is not known on line 22 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

Could I please have help deleting this nonsense wine deb and restoring all the indexes I got when I installed Ubuntu.Thank you very much. :sad:

---

### Post by Lord Illidan on 2006-07-27
No problemo..

```


## Major bug fix updates produced after the final release of the 
## distribution. 
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted 
 
## Uncomment the following two lines to add software from the 'universe' 
## repository. 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe 
 
## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
# or updates from the Ubuntu security team. 
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
 
deb http://security.ubuntu.com/ubuntu dapper-security main restricted 
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted 
deb http://security.ubuntu.com/ubuntu dapper-security universe 
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by PingunZ on 2006-07-27
Do [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
For an automated source list, great great great app ;)

Oh btw, Ron just add deb before that wine link in line 22 ;)

---

### Post by RonB123123 on 2006-07-27
Lord Illidan, I just add all those and it will fix the error I'm facing with the Wine deb?

PingunZ, I'm not sure how to use what you told me. :( 

And I have no idea how to edit, remove, add or whatever to the wine link. That is half my problem. I think Lord Illidan fixed the other half. 

Thank you for the posts, but I'm still not sure how to remove the deb wine from that list. Someone please post. This is so agravating. I wish every setting had a Default switch lol. All you do is push that button and all the default settings in that pane would be restored. :p

---

### Post by gingermark on 2006-07-27
All your repositories are listed in a text file called "sources.list", which is located in /etc/apt.

Lord Illidan posted a default sources.list (I believe you asked to get things back to how they were when you first installed Ubuntu).

PingunZ's link allows you produce a customised sources.list based in what repositories you want.

At any rate, do ```
gksudo gedit /etc/apt/sources.list
``` to edit the file. You can then add "deb" in front of the WINE line, or do any of the other suggestions. Once you are finished, save the flle and do ```
sudo apt-get update
``` to use your new sources.list file.

---

### Post by RonB123123 on 2006-07-28
Thank you so much everyone, I fixed the deb files and now I do not get that error anymore. Thank you! :D

---

### Post by PingunZ on 2006-07-28
That was an easy one RonTheCon, I hope we can keep helping help you :p

---

