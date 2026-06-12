---
title: "Cannot Install NdisWrapper in Fiesty"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by jkarns on 2007-08-08
I am going out of my mind here. I can't get ndiswrapper in to install. 

jeremy@laptop:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
[B]Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]
jeremy@laptop:~$ 

I also cannot install using Synaptic

What the heck is going on here?????? Frustrating me beyond belief!!

---

### Post by overdrank on 2007-08-08
> **jkarns said:**
> I am going out of my mind here. I can't get ndiswrapper in to install. 

jeremy@laptop:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
[B]Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]
jeremy@laptop:~$ 

I also cannot install using Synaptic

What the heck is going on here?????? Frustrating me beyond belief!!

HI do you get any errors when running update?
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by jkarns on 2007-08-09
> **overdrank said:**
> HI do you get any errors when running update?
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Do you want to continue [Y/n]? y
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)
jeremy@laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)
jeremy@laptop:~$ 



STILL CAN'T INSTALL!! PLEASE HELP!

---

### Post by misfitpierce on 2007-08-09
Maybe try installing with automatix... It pre-configures all its packages and comes with ndiswrapper.

[http://getautomatix.com](http://getautomatix.com)

---

### Post by RomeReactor on 2007-08-09
Hi **jkarns**. Do you have a wired connection at the moment? If so, try purging the **clvm** package first and then reinstalling it:
```
sudo apt-get remove --purge clvm
```
then
```
sudo apt-get update
```
and after that
```
sudo apt-get install clvm
```
Also notice that **ndiswrapper-common** is already installed:
> ndiswrapper-common is already the newest version.
what you need now is **ndiswrapper-utils**.

---

