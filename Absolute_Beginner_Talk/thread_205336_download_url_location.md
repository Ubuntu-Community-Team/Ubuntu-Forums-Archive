---
title: "download url location?"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by crazyoldman1 on 2006-06-28
i am having a ton of trouble with getting updates for Ubuntu and one person sugested to take off the "us" in the urls that download the the updates. 

1.) Well, i went into terminal and used the "sudo aptitude" command to bring up the new console 

2.) then i went to "options > miscellanious"

3.) this is the url i got where it says "url to use to download" =

"[http://cgi.debian.org/cgi-bin/get-changelog?package=%s]("http://cgi.debian.org/cgi-bin/get-changelog?package=%s")" 

Could someone please verify that this is the correct url and that i do not have the incorrect url to download updates and install programs.

If someone has a diffrent URL could they please post it. 

Thanks guys for your help,

crazyoldman 

Also, if anyone has any other ideas could they please post

---

### Post by Dr. Nick on 2006-06-28
instead of looking through aptitude for the url run this command from a terminal and post back here 

cat /etc/apt/sources.list

that file controls your repos for programs/updates

the url you posted is on debian.org and doesnt mention ubuntu, so that may not be the one your looking for. Maybe its an old hompage for aptitude??

---

### Post by crazyoldman1 on 2006-06-28
first thankyou for your help,

I entered the command into terminal and this is what returned

```

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe


```

thanks again,

crazyoldman

yeah i am not sure wht that url is either in the consol

---

### Post by Dr. Nick on 2006-06-28
Ok I believe that is the us you are looking to remove,

Just open that file as sudo in a text editor and remove the "us" on the first line

It should look something like this
```

deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricted
``` 
the "universe" is the repository with all the unsupported applications in it. It is nice to have, but not necessary.

You can just run 

gksudo gedit /etc/apt/sources.list 

if your in gnome

---

### Post by crazyoldman1 on 2006-06-28
i opened up the file in a text editor and  tried to save it but it said i do not have the ability to change or move or delete. Is there a way to remove this setting so i can change the file?

thanks, 
crazyoldman

---

### Post by Dr. Nick on 2006-06-28
ah, you have to launch the text editotr as sudo to be ale to modify it. Try the "gksudo" line above in a terminal.

once you get that done run this command from a terminal to activate the new list

sudo apt-get update

---

### Post by crazyoldman1 on 2006-06-28
well that fixed some of my errors but it did not fix all of them i still get this 1 error telling me that it could only get 11 of the 18 files downloaded but it also said that the repositories might no longer be suported so ill just take that as my answer. 

Thanks for your help,

crazyoldman

---

