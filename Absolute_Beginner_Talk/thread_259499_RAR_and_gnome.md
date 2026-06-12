---
title: "RAR and gnome"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by uncleclinto on 2006-09-17
I'm trying to find a program for gnome to open rar archives.  All the ones on the applications list say they're for KDE.  That means it won't work in gnome right??

---

### Post by picpak on 2006-09-17
I believe that File-Roller will open them. It's installed by default.

---

### Post by jordanmthomas on 2006-09-17
Enable multiverse / universe 
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

```
sudo apt-get update
sudo apt-get install unrar

```

Now, Gnome should open rar files with the default archive manager

---

### Post by uncleclinto on 2006-09-17
I wish it were that easy.  As usual, I've hit a snag:

"admin@WaltersWeb:~$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate"

What the heck does all that mean??

---

### Post by jordanmthomas on 2006-09-17
DId you add the repositories like the ubuntuguide suggests?
Press Alt + F2
type
```
gksu gedit /etc/apt/sources.list
```
Go through the file and for lines that read something like this:
```
 **# deb** .....
```
take out the #
Save and exit.
Then, try again.

Also, if you had already followed the directions, did you
```
sudo apt-get update
```
first?

---

### Post by uncleclinto on 2006-09-17
Yes, I had done sudo apt-get updat.  No, I hadn't uncommented out those lines.  Now, I have.  I updated again (sudo apt-get update).  Here's the message I got:

admin@WaltersWeb:~$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate


Here's what the /etc/apt/sources.list looks like:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
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

---

### Post by jordanmthomas on 2006-09-17
Well, if you have enabled multivese and done 
```
sudo apt-get update
```
There is no reason you shouldn't be able to get unrar.
You could always download it manually and install it.

[http://packages.ubuntu.com/dapper/utils/unrar](http://packages.ubuntu.com/dapper/utils/unrar)

---

### Post by konst88 on 2006-09-17
try:
sudo aptitude install unrar

it will try to solve dependecies problems.

---

