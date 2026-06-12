---
title: "RPM install problem"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by hwe001 on 2006-05-26
I am install a software packaged in RPM format. when I ran:

rpm -ivh blah.rpm

it gives me such error message:

rpm: To install rpm packages on Debian systems, use alien....
error: cannot open Pacakges index using db3..

why is that? my system is Ubuntu not Debian!

---

### Post by kart3r on 2006-05-26
Your half right i think ubuntu is not debian but is based on it.RPM packages can't be installed on ubuntu but you can do it doing this:
apt-get install alien
sudo alien -i /location/file.rpm

alien transforms the rpm package ina debian package but i'm not sure if it installs automatically.search for wiki about alien

---

### Post by Perfect Storm on 2006-05-26
Have you tried with alien?

Also have you checked for a .deb package?

---

### Post by jethro10 on 2006-05-26
There are two main types of packages for installation on linux, .rpm and .deb, Ubuntu used the .deb style packages and Ubuntu is infact a Debian based version of Linux.

alien is a program that will convert an .rpm to a .deb package that you can then install correctly.

I think its in the repositories but you will need to run it on a command line !!! to convert the rpm to deb.

Jeff

---

