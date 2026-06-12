---
title: "cd /var/lib/dpkg/info is non existent"
date: 2011-04-15
forum: Any Other OS
---

### Post by johnnyw on 2011-04-15
Hi guys I have a missing  cd /var/lib/dpkg/info. Ive been browsing all around the web with no clue.

Ive got Mint with fluxbox


Appreciate

EDIT:

```

sudo aptitude update && aptitude -y safe-upgrade


Initializing package states... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?



sudo apt-get install chromium
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  chromium-bsu chromium-bsu-data libalut0 libglc0 libglpng ttf-uralic
The following NEW packages will be installed:
  chromium chromium-bsu chromium-bsu-data libalut0 libglc0 libglpng ttf-uralic
0 upgraded, 7 newly installed, 0 to remove and 49 not upgraded.
Need to get 2,184kB of archives.
After this operation, 4,268kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libalut0 libglc0 libglpng chromium-bsu-data ttf-uralic chromium-bsu chromium
Authentication warning overridden.
Get:1 [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid/universe libalut0 1.1.0-2 [32.3kB]
Get:2 [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid/universe libglc0 0.7.2-1 [77.0kB]
Get:3 [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid/universe libglpng 1.45-6 [9,920B]
Get:4 [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid/universe chromium-bsu-data 0.9.14-1 [1,241kB]
Get:5 [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid/universe ttf-uralic 0.0.20040829-1ubuntu2 [684kB]                                                          
Get:6 [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid/universe chromium-bsu 0.9.14-1 [126kB]                                                                     
Get:7 [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) lucid/universe chromium 0.9.14-1 [13.9kB]                                                                        
Fetched 2,184kB in 14s (147kB/s)                                                                                                                            
dpkg: cannot scan updates directory `/var/lib/dpkg/updates/': No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by wolfen69 on 2011-04-15
```
sudo mkdir /var/lib/dpkg/updates
```
then
```
sudo chmod 755 /var/lib/dpkg/updates
```
then
```
sudo apt-get update
```

---

### Post by Perfect Storm on 2011-04-16
Moved to Other OS/Distro talk.

---

### Post by johnnyw on 2011-04-16
> **wolfen69 said:**
> ```
sudo mkdir /var/lib/dpkg/updates
```
then
```
sudo chmod 755 /var/lib/dpkg/updates
```
then
```
sudo apt-get update
```

Many thanks man.

here is what happened.

all went fine but the upgrade got wrong.

sudo apt-get upgrade


Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by johnnyw on 2011-04-17
what can I do?

thanks

---

### Post by johnnyw on 2011-04-18
Im now getting this error:

[http://bit.ly/hra7sZ](http://bit.ly/hra7sZ)

---

### Post by johnnyw on 2011-04-19
Can someone please aid me in this issue?

Appreciate

---

### Post by wolfen69 on 2011-04-20
Try
```
sudo dpkg --clear-avail && sudo apt-get update
```

---

### Post by johnnyw on 2011-04-27
thx wolf.

I now see :

 sudo apt-get install uml-utilities bridge-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package uml-utilities is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package uml-utilities has no installation candidate


and this:

[IMG]http://i.imgur.com/ti47p.png[/IMG]

---

### Post by johnnyw on 2011-04-28
elvis1@elvis1-desktop /tmp $ sudo dpkg -i uml-utilities_20070815-1.1_i386.deb


this is part of the output ( long list) . I bet Ive fubared the OS

[http://pastebin.com/6mktifwx](http://pastebin.com/6mktifwx)




[http://i.imgur.com/OjwFs.png](http://i.imgur.com/OjwFs.png)
[http://i.imgur.com/RkjnD.png](http://i.imgur.com/RkjnD.png)

when I tried to install the dependencies from the uml utilities, more and more popped out.

thx

---

### Post by johnnyw on 2011-04-28
any clue of how to solve this?

appreciate

---

### Post by johnnyw on 2011-04-29
guys should I format then?

---

