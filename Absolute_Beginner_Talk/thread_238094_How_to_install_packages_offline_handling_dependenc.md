---
title: "How to install packages offline handling dependencies"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by uthpalawe on 2006-08-17
Hi,
  I am using Ubuntu 5.10 and I need to install some new software(I have only 128MB of RAM). I  do not have a direct internet connection but I can access it. 
  So what I plan to do is download the package with all its dependencies and use the saved files to install the packages. But I am not sure where it is possible.

1. The first is it possible to download all dependencies using apt-get -d option? **OR** will it download the packages needed to that specific machine? Is there any windows utilities for doing this?

2.  After I download the need file what is the next thing I have to do?
  Sorry for the trouble. Thanks.

---

### Post by hotbrainz on 2006-08-17
hey dude,

Go to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
and get the packages u need. and then do the following:

Download the packages you want.
Burn them on a cd.
Pop it into your Ubuntu box.
Go to System > Administration > Synaptic Package Manager
Go to Edit > Add CD-ROM
Add it as a source.
Go to Settings > Repositories
Uncheck every box except the one you just added
Click Reload
Search for whichever package you want to install from your cd
Mark it for installation.
Apply Changes.

Courtesy : Aysiu


This I did when i was new to Ubuntu

Hope this helps.

Cheers

---

### Post by uthpalawe on 2006-08-18
Thanks for your reply.
But I have some doubts. Is it OK to write the *.deb files just in the root of CD? OR any other files needed to detect them?

Also if I am installing some program that depends on some other programs is there a way to download this once.

hotbrainz, Thanks for your comment definatly I'll be opening doors for Linux.

---

