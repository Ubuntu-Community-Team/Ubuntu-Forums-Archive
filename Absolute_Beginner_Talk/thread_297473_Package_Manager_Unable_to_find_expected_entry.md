---
title: "Package Manager: Unable to find expected entry"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by happyisland on 2006-11-11
Hey all,
Ok, I am getting the following error when I get the package manager to check for what new stuff is available:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://ubuntu.moshen.de/dists/dapper/Release:](http://ubuntu.moshen.de/dists/dapper/Release:) Unable to find expected entry  flash/binary-amd64/Packages in Meta-index file (malformed Release file?)

Could someone please give me some advice on how to take care of this in a way that won't deprive me of future updates or otherwise bork my system?

Thanks!
HI

---

### Post by qscgz on 2006-11-11
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

especially:

[https://help.ubuntu.com/community/Repositories#head-9067080b61c44973ed11e270ba73fe4ec8ed05a0](https://help.ubuntu.com/community/Repositories#head-9067080b61c44973ed11e270ba73fe4ec8ed05a0)

[https://wiki.ubuntu.com/FindPage](https://wiki.ubuntu.com/FindPage) 

Check your repositories, please.

---

### Post by happyisland on 2006-11-11
Checked 'em. 
Thanks for the links, but the thing is, I'm not sure why this is in my repositories list in the first place. I'm guessing it got there during an Automatix2 flash install, but I'm not positive. I guess my question was more specific: how would removing this repository impact my system?
Sorry if this is too beginnerish, but that's why I chose this forum to post it in.
Thanks,
HI

---

### Post by qscgz on 2006-11-12
There is only a waranty for the Ubuntu "main", "restricted" repositories to get security updates and program upgrades for 3 years (6.06 LTS desktop) 5 years (6.06 LTS server) and 18 months for others.

All non-Ubuntu repositories will be managed by the regarding maintainer.

>I'm guessing it got there during an Automatix2 flash install, but I'm not positive. 

>I guess my question was more specific: how would removing this repository impact my system?

You will not be capable to get any security and upgrade notifications (if there will be one) provided by the regarding repository source/server.

---

### Post by wesley_of_course on 2006-12-16
Hope this the right forum and with almost identical problems assume it is . 


wesley@RatDog:~$ sudo apt-get update

Fetched 8B in 1s (6B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release)  Unable to find expected entry  deb/source/Sources in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
  
   After going here ;   	[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
  then here ; Managing Repositories from the Command Line 
         I had tried this numerous times and over the course of a few days and couldn't seem to make it work , was hoping I had missed something which was why it was a few days.(Sleep , work , try again when I got home ) , but at the bottom of this page I found a link ,  [WWW] [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)  ! Eureka !,  so I  ~

wesley@RatDog:~$ sudo gedit /etc/apt/sources.list
  
   deleted that list and inserted this one from [WWW] [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
which generated this ; 
# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse


    I don't recall seeing this ,# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -,at the top of my /etc/apt/sources.list , but it might have very 
  well had been there ! Incidentially it seemed like it all started with Automatix but not sure if it was the added repository's or not ,it was probably my own error somewhere along the way , ( starting to drift here , focus ) , short storie - it worked . Long story - ran 
wesley@RatDog:~$ sudo apt-get update
wesley@RatDog:~$ sudo aptitude update
   
   Now about that upgrade .,.,.,.,.,.,.,.,.,.,????????  :-k

---

