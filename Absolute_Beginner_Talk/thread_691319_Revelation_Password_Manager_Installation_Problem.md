---
title: "Revelation Password Manager Installation Problem"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by wrgarrett on 2008-02-08
I am 1 week new to Ubuntu and I am trying to install Revelation Password Manager.
I go to the site [http://archive.ubuntulinux.org/ubuntu/pool/universe/r/revelation/](http://archive.ubuntulinux.org/ubuntu/pool/universe/r/revelation/) and select 
[http://archive.ubuntulinux.org/ubuntu/pool/universe/r/revelation/revelation_0.4.11-2ubuntu2_i386.deb](http://archive.ubuntulinux.org/ubuntu/pool/universe/r/revelation/revelation_0.4.11-2ubuntu2_i386.deb)
and choose Open with GDebi Package Installer. I then get a window open with Error: Dependency is not satisfiable: libc 6.

I searched the forum for this term and got confusing results. One of which was why was the user not using the Synaptic Package Manager. So I looked and Revelation is not listed. Does this mean this app is not available for Ubuntu 6.06, which is what I have, I guess, that is what shows under System>About Ubuntu? 

If not usable on Ubuntu, does anyone know of a password manager that is?

Thanks, and I apologize in advance for my noobieness but I gotta start somewere!

---

### Post by taurus on 2008-02-08
Not sure about 6.06 but it is available in the repos for 7.10.  See if it is available for installing if you run

```
sudo apt-get update
sudo apt-get install revelation
```

---

### Post by wrgarrett on 2008-02-08
Ok, here is what happend:

william@william-laptop:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release [50.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages [265kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages [6378B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources [72.8kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [983B]
Fetched 396kB in 3s (113kB/s)
Reading package lists... Done
william@william-laptop:~$ sudo apt-get install revelation
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package revelation
william@william-laptop:~$

---

### Post by hyper_ch on 2008-02-08
use apt-cache for searching.

---

### Post by taurus on 2008-02-08
> **wrgarrett said:**
> Ok, here is what happend:

william@william-laptop:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release [50.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages [265kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages [6378B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources [72.8kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [983B]
Fetched 396kB in 3s (113kB/s)
Reading package lists... Done
william@william-laptop:~$ sudo apt-get install revelation
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package revelation
william@william-laptop:~$

Revelation is in the universe repo so make sure you have that enable in /etc/apt/sources.list.

Edit /apt/sources.list 

```
gksudo gedit /etc/apt/sources.list
```
and remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and then run

```
sudo apt-get update
sudo apt-get install revelation
```
Otherwise, here is it.

[http://packages.ubuntu.com/dapper/gnome/revelation](http://packages.ubuntu.com/dapper/gnome/revelation)

---

### Post by wrgarrett on 2008-02-12
> **taurus said:**
> 
Otherwise, here is it.

[http://packages.ubuntu.com/dapper/gnome/revelation](http://packages.ubuntu.com/dapper/gnome/revelation)

Got it! Thanks!:)

---

