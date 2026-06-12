---
title: "My sources.list file is gone.. ???"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-10
Hello,

when I try to open sources.list file in terminal, it's totally empty. However, there were lots of links there before. Furthermore, if I place new links there and try to save,  iget the message the can't save the file: file couldn't be found. what should I do? without that I can't install anything in terminal, I always get the same message: 

E: Malformed line 1 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.

there's another file, sources.list.copy and there's everything ok, all  the links are there. but if I try to open it with terminal or copy it to sources.list, I get error message:

sudo cp /etc/apt/sources.list.copy /etc/apt/sources.list
Password:
cp: cannot stat `/etc/apt/sources.list.copy': No such file or directory

what should I do?

---

### Post by picpak on 2007-04-10
Can you please post the output of this command?

```
cat /etc/apt/sources.list
```

---

### Post by taurus on 2007-04-10
What's the output of this command from a terminal?

```
ls -la /etc/apt
```
Otherwise, create a new one with

```
gksudo gedit /etc/apt/sources.list
```
and here are the repos.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by O-pos on 2007-04-10
Output of cat /etc/apt/sources.listdeb:

```
 http://sadleder.de/debian/gimp_2.3.10-1.1_i386.deb
deb http://sadleder.de/debian/gimp-data_2.3.10-1.1_all.deb
deb http://sadleder.de/debian/libgimp2.0_2.3.10-1.1_i386.deb
deb http://ftp.debian.org/debian/pool/main/libw/libwmf/libwmf0.2-7_0.2.8.4-2_i386.deb
deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb ftp://ftp.videolan.org/pub/videolan/ubuntu edgy universe
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb http://cran.at.r-project.org/bin/linux/ubuntu edgy/
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb http://at.archive.ubuntu.com/ubuntu/ edgy main restricted universe
deb-src http://at.archive.ubuntu.com/ubuntu/ edgy main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://at.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe
deb-src http://at.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe

## Uncomment the following two lines to add software from the ## 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://at.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://at.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://at.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://at.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe 
```

output of ls -la /etc/apt:

```

total 40
drwxr-xr-x   4 root root 4096 2007-04-09 19:23 .
drwxr-xr-x 106 root root 4096 2007-04-10 21:01 ..
drwxr-xr-x   2 root root 4096 2007-04-03 12:43 apt.conf.d
-rw-------   1 root root    0 2006-10-25 15:27 secring.gpg
-rw-r--r--   1 root root 2490 2007-04-09 19:23 sources.list
-rw-r--r--   1 root root 2491 2007-04-09 19:12 sources.list~
drwxr-xr-x   2 root root 4096 2006-09-28 01:44 sources.list.d
-rw-r--r--   1 root root 2048 2007-04-07 18:47 sources.list.save
-rw-------   1 root root 1200 2006-10-25 15:27 trustdb.gpg
-rw-r--r--   1 root root 2393 2006-10-25 15:27 trusted.gpg
-rw-r--r--   1 root root 2381 2006-10-25 15:27 trusted.gpg~ 
```

apt.conf.d & sources.list.d appear in bold blue color, It's first time I see another color than black in my terminal.

I just had another question: does the above mentioned code contain "extra repositories"? I was trying to install video codecs and that was a prerequiment..

---

### Post by taurus on 2007-04-10
Not sure why you have the first four lines in your /etc/apt/sources.list since they are wrong.  Therefore, you need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the first four lines.

```

 http://sadleder.de/debian/gimp_2.3.10-1.1_i386.deb
deb http://sadleder.de/debian/gimp-data_2.3.10-1.1_all.deb
deb http://sadleder.de/debian/libgimp2.0_2.3.10-1.1_i386.deb
deb http://ftp.debian.org/debian/pool/main/libw/libwmf/libwmf0.2-7_0.2.8.4-2_i386.deb

```
Also, may want to place a # in front of these two lines to comment them out.

```
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
#deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
```
Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by O-pos on 2007-04-10
Thanks :) , it works :) :) . upgrade is running now... it seems to take much time and in 2 hours the wireless at my student's house is shout down. Can it be a problem if it's not complete till then?

Another question: could you tell me whether extra repositories are included in my sources.list? I need it for downloading video codecs..

Thanks again :)

---

### Post by sailor2001 on 2007-04-10
automatix or automatix2 if you are in edgy has your codecs

---

### Post by taurus on 2007-04-10
Just edit /etc/apt/sources.list again

```
gksudo gedit /etc/apt/sources.list
```
and remove the # in front of all the lines that start with **deb** (except the two lines that have cdrom in them).  That would enable universe and multiverse for you.

Then, use this guide to install codecs or whatnot.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

