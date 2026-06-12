---
title: "Problem with Add/Remove and Software Properties"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by MJL on 2006-09-06
Hi all,

   I am really new to Ubuntu and cannot get either Add/Remove or Software Properties to work. Using the command line I get these messages...

```
auser@ausercomp:~$ gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 20, in ?
    from AppInstall.AppInstall import AppInstall
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 62, in ?
    from SoftwareProperties.aptsources import SourcesList, is_mirror
ImportError: cannot import name SourcesList

auser@ausercomp:~$ gksu /usr/bin/software-properties
  File "/usr/bin/software-properties", line 78, in ?
    app = SoftwareProperties.SoftwareProperties(data_dir, options, file)
AttributeError: 'module' object has no attribute 'SoftwareProperties'
```

Could anyone point me in the right direction to fix this?

MJL

---

### Post by xyz on 2006-09-06
Hi-
When you click on Application (at the top left of your screen) and scroll all the way down, doesn't "Add/Remove"show? Then simply clicking on it should make it appear!

---

### Post by petri on 2006-09-06
I'm not sure but for me it seems like you are not new to Linux :D 

Here you can find som documentation to get you going: [http://www.ubuntu.com/support/documentation](http://www.ubuntu.com/support/documentation)

---

### Post by petri on 2006-09-06
I'm not sure but for me it seems like you are not new to Linux :D 

Here you can find som documentation to get you going: 

[http://www.ubuntu.com/support/documentation](http://www.ubuntu.com/support/documentation)
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by Sef on 2006-09-06
Has this problem existed since you installed the system, or has it occurred after you did something?

> ImportError: cannot import name SourcesList

Could you post your sources.list

Applications > Accessories > Terminal

sudo gedit /etc/apt/sources.list

---

### Post by MJL on 2006-09-06
I installed Ubuntu just a few days ago. When I used the Applications menu to try Add/Remove or Software Properties, nothing appeared at all. I used the command line to try to see any errors that occurred. I don't know how to resolve messages I saw and posted.

Thank you for the links. I will look through them now.

MJL

---

### Post by MJL on 2006-09-06
Sef, here is my sources.list

```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

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
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```

---

