---
title: "where can i get the package and repo?not from ftp side~~"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by penguinKabuki on 2006-08-12
where can i get the package and repo....besides from ftp side?
i really need to know this because...everytime i want to install something.....it will say....no package available.

---

### Post by penguinKabuki on 2006-08-12
and also............
i dont understand.............why.......i always get problems like this.........
==========
penguin@penguin-desktop:~$   sudo apt-get install sun-java5-bin
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-bin
penguin@penguin-desktop:~$
==============

couldnt find package?

---

### Post by Jagot on 2006-08-12
Do you have the multiverse repository enabled?  That is where Java is.  If not, see either of these links:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by penguinKabuki on 2006-08-12
i already enable the manage repo........
but the same problems happen...
here...i attach the print screen~~

---

### Post by Jagot on 2006-08-12
I can't see the multiverse repo.  Could you post the output of this command:

```
cat /etc/apt/sources.list
```

---

### Post by penguinKabuki on 2006-08-12
heres the output.........

===========
# Line commented out by installer because it failed to verify:
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
===========

---

### Post by Jagot on 2006-08-12
OK, I suggest you replace that sources.list with the one in the psychocats link above.  The multiverse repo in your sources.list is only in backports which is not where the files you need are.

---

### Post by penguinKabuki on 2006-08-14
dear people........

i try to change the source code....but then again...i face problems.

i put 

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
 kdesu kwrite /etc/apt/sources.list

in the terminal...

but what happen is........<---i attach the print screen.

and...where can i paste the new coding for my source code?

this what i got when i use the root access..
===============
penguin@penguin-desktop:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
penguin@penguin-desktop:~$ sudo -i
Password:
root@penguin-desktop:~# sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
root@penguin-desktop:~#  kdesu kwrite /etc/apt/sources.list
kdesu: cannot connect to X server
root@penguin-desktop:~#
===============

---

### Post by penguinKabuki on 2006-08-21
abt the source.list..........
is it we delete the existing and add the new coding..or we leave the existing...and add new coding?

i add the new coding.......
and i still face the same problems.......

----------
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-bin
------------

---

