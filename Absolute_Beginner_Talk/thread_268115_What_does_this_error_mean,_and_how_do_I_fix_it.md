---
title: "What does this error mean, and how do I fix it??"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2006-09-29
Hi everybody,

Can anybody help me with this error (see screenshot). It has been hanging me up for over 24 hours and it's starting to drive me crazy.

Thanks,

KC

Okay, I'm really losing it now! This thing won't let me download a screenshot.

I guess I'll try it a different way.

carbonfish@carbonfish-laptop:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
The following packages will be upgraded:
  bind9-host dnsutils firefox firefox-gnome-support gzip libbind9-0 libdns21
  libgnutls12 libisc11 libisccc0 libisccfg1 liblwres9 libnspr4 libnss3
  libssl0.9.8 libxfont1 linux-386 linux-image-2.6.15-26-386
  linux-restricted-modules-2.6.15-26-386 linux-restricted-modules-common
  mozilla-thunderbird openssl
22 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/54.5MB of archives.
After unpacking, 111kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `libgtkmm-2.4-1c2a': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
carbonfish@carbonfish-laptop:~$

This is what happens when I use the Terminal. It is the same error I get with Synaptic.

I am stuck.. Please help if you can.

Thanks

---

### Post by nudnik on 2006-09-29
> **Carbonfish said:**
> Hi everybody,

Can anybody help me with this error (see screenshot). It has been hanging me up for over 24 hours and it's starting to drive me crazy.

Thanks,

KC

Verily, thy screenshot is missing:-#

---

### Post by Carbonfish on 2006-09-29
Yeah... Thanks nudnik. I don't know why I can't upload a screenshot. It asks me what I want to use to open the .png file, a text editor or other.. I have never had any trouble attaching a screenshot before.

Anyway, I copied and pasted the error message that is the same as the one that comes up in Synaptic.

KC

---

### Post by thephantomlinguist on 2006-09-29
Have you tried a ```
sudo apt-get -f install
```?

---

### Post by Carbonfish on 2006-09-29
Hi thephantomlinguist,

Tried your suggestion. Got this.

carbonfish@carbonfish-laptop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
carbonfish@carbonfish-laptop:~$

---

### Post by Carbonfish on 2006-09-29
Is there any way that I can get apt-get to ignore the package:  /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb?

Or is there any way that I can "force" the upgrade/install?

I can't live with that update icon on my system panel forever and I want to be able to know what condition my system is in...

Anybody?

---

### Post by thephantomlinguist on 2006-09-29
If you can't stand the icon, you can turn it off.

I'd give you a link, but I've gotta run. Search around on the forums--someone's bound to have posted a miniHowTo.

Hope this helps!

---

### Post by Carbonfish on 2006-09-29
> **thephantomlinguist said:**
> If you can't stand the icon, you can turn it off.
Hope this helps!

That's a ridiculous and *not* at all helpful suggestion. I am trying to resolve this problem, not ignore it..:evil:

Does anyone have any suggestions other than closing my eyes and hoping the problem goes away?

TIA

KC

---

### Post by sbergman27 on 2006-09-29
> **Carbonfish said:**
> Hi everybody,

Can anybody help me with this error (see screenshot). It has been hanging me up for over 24 hours and it's starting to drive me crazy.


Bad file in the cache?

Try:

```

sudo apt-get clean
sudo apt-get update

```

---

### Post by thephantomlinguist on 2006-09-29
> **Carbonfish said:**
> That's a ridiculous and *not* at all helpful suggestion. I am trying to resolve this problem, not ignore it..:evil:

I misunderstood you. (I can't live with that update icon on my system panel forever...)

My apologies...

---

### Post by Carbonfish on 2006-09-29
We may have both mis-understood each other. I am a bit frazzled and have a bit of a short fuse about this problem as I have been trying without success to resolve it since yesterday. Apology accepted, and if I was a bit snarley I apologise myself.

KC

Okay, after trying just about everything I can think of I have discovered that out of the 26 updates that the update manager says are available, none of them will install. If I de-select them one at a time, they each give me the same error in turn, only the package name is different.

Any ideas how I can get this update out of my system and start over without doing a complete fresh install???

PLEASE??

---

### Post by pbaehr on 2006-09-29
Have you tried aptitude? Sometimes I have problems with apt-get and aptitude does it no problem.

Try:
```

sudo aptitude update
sudo aptitude dist-upgrade

```

Maybe it will give you the same error, but maybe it will be successful. It is a little bit more sophisticated than apt-get.

Good luck...

---

### Post by Carbonfish on 2006-09-29
> **pbaehr said:**
> Have you tried aptitude? Sometimes I have problems with apt-get and aptitude does it no problem.

Try:
```

sudo aptitude update
sudo aptitude dist-upgrade

```

Maybe it will give you the same error, but maybe it will be successful. It is a little bit more sophisticated than apt-get.

Good luck...

Thaks for trying to help.
Yes I've tried Aptitude. I get the same error. Here is the Terminal output.

carbonfish@carbonfish-laptop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Fetched 3B in 1s (2B/s)
Reading package lists... Done
carbonfish@carbonfish-laptop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  linux-image-2.6.15-27-386 linux-restricted-modules-2.6.15-27-386
The following NEW packages will be installed:
  linux-image-2.6.15-27-386 linux-restricted-modules-2.6.15-27-386
The following packages will be upgraded:
  bind9-host dnsutils firefox firefox-gnome-support gzip libbind9-0
  libdns21 libgnutls12 libisc11 libisccc0 libisccfg1 liblwres9 libnspr4
  libnss3 libssl0.9.8 libxfont1 linux-386 linux-image-2.6.15-26-386
  linux-image-386 linux-restricted-modules-2.6.15-26-386
  linux-restricted-modules-386 linux-restricted-modules-common
  mozilla-thunderbird openssl
24 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/84.4MB of archives. After unpacking 84.5MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `libgtkmm-2.4-1c2a': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
carbonfish@carbonfish-laptop:~$

---

### Post by ashokpappu on 2006-09-29
try removing the offending package with apt and see if the problem goes away.

---

### Post by sbergman27 on 2006-09-29
> **ashokpappu said:**
> try removing the offending package with apt and see if the problem goes away.

No!!!!

Don't remove gzip!!!!

That will break dpkg and apt, won't it?

---

### Post by Carbonfish on 2006-09-29
> **ashokpappu said:**
> try removing the offending package with apt and see if the problem goes away.

Thanks for trying to help.. Here's what I get.

carbonfish@carbonfish-laptop:~$ sudo apt-get remove gzip_1.3.5-12ubuntu0.1_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gzip_1.3.5-12ubuntu0.1_i386.deb
carbonfish@carbonfish-laptop:~$ sudo apt-get remove /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package
carbonfish@carbonfish-laptop:~$

The problem is happening *before* the package is installed.

Like I mentioned in an earlier post, every package in the update/upgrade does the same thing. If I select only one of the packages in the update/upgrade I get the same error: "failed in the buffer_read(fd)"

](*,) ](*,) ](*,)

There are 916 hits in Google for failed in the buffer_read, so I wouldn't even know where to start. *shrugs shoulders, slumps in chair and sighs*

KC

---

### Post by sbergman27 on 2006-09-29
Did you try:

sudo apt-get clean
sudo apt-get update

You never mentioned.  And this could easily be a bad package in the cache.

-Steve

---

### Post by bulldog on 2006-09-29
Well in my humble opinion is uninstalling or removing not too dangerous because it's an archieve.

I should try to uninstall it but make a backup first [it's broken but you never know]

And see if overcome the problem.

Did you look in your synaptic if there any broken packages btw?

---

### Post by Carbonfish on 2006-09-29
> **sbergman27 said:**
> Did you try:

sudo apt-get clean
sudo apt-get update

You never mentioned.  And this could easily be a bad package in the cache.

-Steve

Hi Steve, 

Yes I did. Here is what I get after the sudo apt-get clean and sudo apt-get update..

carbonfish@carbonfish-laptop:~$ sudo apt-get clean update
carbonfish@carbonfish-laptop:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Fetched 3B in 1s (2B/s)
Reading package lists... Done
carbonfish@carbonfish-laptop:~$

But here is what I get if I try to upgrade...

carbonfish@carbonfish-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
The following packages will be upgraded:
  bind9-host dnsutils firefox firefox-gnome-support gzip libbind9-0 libdns21
  libgnutls12 libisc11 libisccc0 libisccfg1 liblwres9 libnspr4 libnss3
  libssl0.9.8 libxfont1 linux-386 linux-image-2.6.15-26-386
  linux-restricted-modules-2.6.15-26-386 linux-restricted-modules-common
  mozilla-thunderbird openssl
22 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 54.5MB of archives.
After unpacking, 111kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main gzip 1.3.5-12ubuntu0.1 [71.2kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libgnutls12 1.2.9-2ubuntu1.1 [373kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libssl0.9.8 0.9.8a-7ubuntu0.2 [2594kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libisc11 1:9.3.2-2ubuntu1.1 [172kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libdns21 1:9.3.2-2ubuntu1.1 [478kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libisccc0 1:9.3.2-2ubuntu1.1 [90.4kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libisccfg1 1:9.3.2-2ubuntu1.1 [102kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libbind9-0 1:9.3.2-2ubuntu1.1 [91.0kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main liblwres9 1:9.3.2-2ubuntu1.1 [107kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main bind9-host 1:9.3.2-2ubuntu1.1 [108kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main dnsutils 1:9.3.2-2ubuntu1.1 [175kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main firefox-gnome-support 1.5.dfsg+1.5.0.7-ubuntu0.6.06 [75.0kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libnspr4 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06 [147kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libnss3 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06 [670kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06 [7925kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libxfont1 1:1.0.0-0ubuntu3.2 [216kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-386 2.6.15.25 [23.4kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-image-2.6.15-26-386 2.6.15-26.47 [21.7MB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-modules-common 2.6.15.11-5 [17.9kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-modules-2.6.15-26-386 2.6.15.11-4 [8138kB]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main mozilla-thunderbird 1.5.0.7-0ubuntu0.6.06 [10.3MB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main openssl 0.9.8a-7ubuntu0.2 [976kB]
Fetched 54.5MB in 5m48s (156kB/s)
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `libgtkmm-2.4-1c2a': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
carbonfish@carbonfish-laptop:~$

---

### Post by sbergman27 on 2006-09-29
> **bulldog said:**
> Well in my humble opinion is uninstalling or removing not too dangerous because it's an archieve.


apt-get/dpkg needs gunzip to install packages.  gunzip is part of the gzip package.  If you uninstall the gzip package, there is no way to reinstall it, or any other package, and you're dead in the water.

Actually, apt won't let you uninstall it without jumping through a couple of hoops.

---

### Post by Carbonfish on 2006-09-29
> **bulldog said:**
> Well in my humble opinion is uninstalling or removing not too dangerous because it's an archieve.

I should try to uninstall it but make a backup first [it's broken but you never know]

And see if overcome the problem.

Did you look in your synaptic if there any broken packages btw?

Yes Bulldog. I checked yesterday, and again just now. There are no broken packages, and if I try through synaptic to mark all of the updates and install them, I get the same error message.

---

### Post by morphodone on 2006-09-29
how about:

```
sudo rm /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb
```

---

### Post by bulldog on 2006-09-29
If you try to install it first completely and then remove it.

Could work or maybe not,but we have to try something.
```
 sudo aptitude install gzip_1.3.5-12ubuntu0.1_i386.deb 
```


EDIT:
Do you have any idea what the package is?

---

### Post by Carbonfish on 2006-09-29
> **morphodone said:**
> how about:

```
sudo rm /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb
```

Thanks for trying...

carbonfish@carbonfish-laptop:~$ sudo rm /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb
Password:
carbonfish@carbonfish-laptop:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Fetched 3B in 1s (2B/s)
Reading package lists... Done
carbonfish@carbonfish-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-image-2.6.15-27-386 linux-restricted-modules-2.6.15-27-386
The following packages will be upgraded:
  bind9-host dnsutils firefox firefox-gnome-support gzip libbind9-0 libdns21
  libgnutls12 libisc11 libisccc0 libisccfg1 liblwres9 libnspr4 libnss3
  libssl0.9.8 libxfont1 linux-386 linux-image-2.6.15-26-386 linux-image-386
  linux-restricted-modules-2.6.15-26-386 linux-restricted-modules-386
  linux-restricted-modules-common mozilla-thunderbird openssl
24 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 71.2kB/84.4MB of archives.
After unpacking, 84.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main gzip 1.3.5-12ubuntu0.1 [71.2kB]
Fetched 71.2kB in 6s (11.6kB/s)
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `libgtkmm-2.4-1c2a': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
carbonfish@carbonfish-laptop:~$


KC

---

### Post by sbergman27 on 2006-09-29
What repositories do you have enabled?  Are we getting a bad package from a repo you have added, I wonder?

---

### Post by Carbonfish on 2006-09-29
> **bulldog said:**
> If you try to install it first completely and then remove it.

Could work or maybe not,but we have to try something.
```
 sudo aptitude install gzip_1.3.5-12ubuntu0.1_i386.deb 
```
EDIT:
Do you have any idea what the package is?

No, I don't have any idea what package it is.

I tried to install the .deb, here's what I got.

carbonfish@carbonfish-laptop:~$ sudo aptitude install gzip_1.3.5-12ubuntu0.1_i386.deb
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "gzip_1.3.5-12ubuntu0.1_i386.deb"
The following packages have been kept back:
  bind9-host dnsutils firefox firefox-gnome-support gzip libbind9-0
  libdns21 libgnutls12 libisc11 libisccc0 libisccfg1 liblwres9 libnspr4
  libnss3 libssl0.9.8 libxfont1 linux-386 linux-image-2.6.15-26-386
  linux-image-386 linux-restricted-modules-2.6.15-26-386
  linux-restricted-modules-386 linux-restricted-modules-common
  mozilla-thunderbird openssl
0 packages upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
carbonfish@carbonfish-laptop:~$

In answer to sbergman27 I have the officially supported, universe, and multiverse repositories enabled I think. How can I find and paste that info., or do you just want my sources list?

---

### Post by bulldog on 2006-09-29
The .deb isn't in the original repo's,synaptic couldn't find it here.

Suppose you downloaded it somewhere,maybe in your /home?

Try to find the package and install it and then you can remove it again,which should be the solution for this trouble.

[I feel for you,it's pretty annoying]

---

### Post by sbergman27 on 2006-09-29
> **Carbonfish said:**
> 
In answer to sbergman27 I have the officially supported, universe, and multiverse repositories enabled I think. How can I find and paste that info., or do you just want my sources list?

I was just wondering if you might have added any custom repos.

To try to install gzip_1.3.5-12ubuntu0.1_i386.deb manually, you can:

```

sudo dpkg -i /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb 

```

It would be interesting to see the results of that.

---

### Post by bulldog on 2006-09-29
> **sbergman27 said:**
> I was just wondering if you might have added any custom repos.

To try to install the gzip_1.3.5-12ubuntu0.1_i386.deb deb manually, you can:

```

sudo dpkg -i /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb 

```

It would be interesting to see the results of that.

The package is a ghost and doesn't exist.:D

---

### Post by Carbonfish on 2006-09-29
> **sbergman27 said:**
> I was just wondering if you might have added any custom repos.

To try to install gzip_1.3.5-12ubuntu0.1_i386.deb manually, you can:

```

sudo dpkg -i /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb 

```

It would be interesting to see the results of that.

Not so much...

carbonfish@carbonfish-laptop:~$ sudo dpkg -i /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb
Password:
Sorry, try again.
Password:
(Reading database ... dpkg: error processing /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb (--install):
 failed in buffer_read(fd): files list for package `libgtkmm-2.4-1c2a': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.5-12ubuntu0.1_i386.deb
Processing was halted because there were too many errors.
carbonfish@carbonfish-laptop:~$

](*,) 

I'll only be able to stay at this for another 20 minutes or so. Then they're going to lock the building around me, but I want to take this opportunity to thank all of you who are taking the time to help me.

If I can't get it figured out tonight, I'll come back and bump this thread tomorrow.;) 

KC

---

### Post by bulldog on 2006-09-29
When I put it in google I get

[http://secunia.com/advisories/22009/](http://secunia.com/advisories/22009/)

Does this mean anything to you?

---

### Post by sbergman27 on 2006-09-29
Well.  Download this:

[http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-12_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-12_i386.deb)

and in the directory you've downloaded it to:

```

sudo dpkg -i gzip_1.3.5-12_i386.deb

```

---

### Post by Carbonfish on 2006-09-29
> **sbergman27 said:**
> Well.  Download this:

[http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-12_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-12_i386.deb)

and in the directory you've downloaded it to:

```

sudo dpkg -i gzip_1.3.5-12_i386.deb

```

Okay, I must be excited or something, but I can't cd to my desktop. I must be making a command line error.

Please don't laugh too hard, but how do I navigate to my desktop?  :oops:

---

### Post by bulldog on 2006-09-29
cd~
cd Desktop

---

### Post by Carbonfish on 2006-09-29
Damn... It didn't work.

carbonfish@carbonfish-laptop:~$ cd~
bash: cd~: command not found
carbonfish@carbonfish-laptop:~$ cd Desktop
carbonfish@carbonfish-laptop:~/Desktop$ sudo dpkg -i gzip_1.3.5-12_i386.deb
Password:
(Reading database ... dpkg: error processing gzip_1.3.5-12_i386.deb (--install): failed in buffer_read(fd): files list for package `libgtkmm-2.4-1c2a': Invalid argument
Errors were encountered while processing:
 gzip_1.3.5-12_i386.deb
Processing was halted because there were too many errors.
carbonfish@carbonfish-laptop:~/Desktop$ cd~
bash: cd~: command not found
carbonfish@carbonfish-laptop:~/Desktop$

I gotta go.  I'll come back to this tomorrow morning. Thanks for all your help.

---

### Post by sbergman27 on 2006-09-29
> **bulldog said:**
> Does this mean anything to you?

Well, the update is a security update due to the fact that several denial of service and potential compromises were found in gzip/gunzip.

What it looks like to me is that the package deb file does indeed exist in /var/cache/apt/archives and is a bad deb.

He ran apt-get clean, which should zap all the files in that directory and download the necessary ones again.

The problem persists, so whatever mirror the deb is getting pulled from is giving him another bad one. (shouldn't the mirrors rotate?)

If the deb from security.ubuntu.org won't install, then I'm out of ideas.  Though it could be a corrupt dpkg database.

I'm actually from the RedHat side of the fence and am more rpm-centric.  Just getting to know apt/dpkg.

On an rpm based distro, it is possible for the rpm database to be rebuilt from scratch with:

```
rpm --rebuilddb
```

No such option seems to exist for dpkg, however.

---

### Post by sbergman27 on 2006-09-29
> **Carbonfish said:**
> 
I gotta go.  I'll come bake to this tomorrow morning. Thanks for all your help.

Good luck!

The package you downloaded installs fine for me.

So the problem lies elsewhere.

In synaptic, try to remove the following package:

libgtkmm-2.4-1c2a

It's the other package mentioned in the error message.  The only dependency that my system has for it is gparted, so it should be ok to remove and reinstall.

Anyway, this will be good ammunition next time an apt crusader tries to convince me that we RedHat users suffer from RPM Hell, whereas apt/dpkg are pure heaven!!!

---

### Post by picpak on 2006-09-29
Let's try getting into some riskier solutions.

I'm assuming you still have gzip_1.3.5-12_i386.deb on your desktop. If not, redownload it.

Then try:

```
sudo dpkg -P --force-depends libgtkmm-2.4-1c2a gzip
sudo dpkg -i ~/Desktop/gzip_1.3.5-12_i386.deb
```

If you need libgtkmm-2.4-1c2a, you can reinstall that too.

---

### Post by Carbonfish on 2006-09-29
> **picpak said:**
> Let's try getting into some riskier solutions.


picpak,

I'm all for it, but I won't have a high speed network available until tomorrow morning PDT. So I can't really make any changes until then (I'm on my iBook now using a dial-up connection... I know, I know.. How primitive).

I'll bump this thread as soon as I get to an open net.

Thanks everyone for the help.

KC

---

### Post by picpak on 2006-09-30
Ok, will wait. But be warned: if you follow my guide, your system removes gzip, and can't get it back, **your system is screwed.**


However, I've used *sudo dpkg -P --force-depends* many a time before, it should work.

---

### Post by sbergman27 on 2006-09-30
> **picpak said:**
> Ok, will wait. But be warned: if you follow my guide, your system removes gzip, and can't get it back, **your system is screwed.**

Picpak,

As mentioned in a previous post, I'm more familiar with rpm than dpkg.  But don't debs contain gzip'd archives?  i.e. isn't it guaranteed that if he uninstalls the gzip package he won't be able to get it, or anything else to install, period?  Or do debs use some other compression/decompression utility?

Before messing with gzip/gunzip, I'd definitely make backup copies of /bin/gzip and /bin/gunzip.  (Which are actually the same binary with different names.)

--
Update:

Yes, a bit of research shows that they are indeed 'ar' archives containing gziped tarballs.

---

### Post by Carbonfish on 2006-09-30
Okay everybody, 

I'm here and ready to fix, or wreck my system. :mrgreen: 

Let the carnage begin.    ;)

sbergmean, what do you think? Should I try to force the gzip package or can anyone think of another alternative before I try?

I have read through Michael Jangs *Linux Patch Management* in the section on apt, but I can't find any approach to a problem like this.

I'm ready. Let's go.

KC

---

### Post by sbergman27 on 2006-09-30
> **Carbonfish said:**
> 
sbergmean, what do you think? Should I try to force the gzip package or can anyone think of another alternative before I try?


I wouldn't.  At this point, I don't think gzip is the problem.  It is more likely corruption in the apt database or a problem with the libgtkmm-2.4-1c2a
 package.

I'd try reinstalling that package with synaptic first.

---

### Post by Carbonfish on 2006-09-30
> **sbergman27 said:**
> I wouldn't.  At this point, I don't think gzip is the problem.  It is more likely corruption in the apt database or a problem with the libgtkmm package.

I'd try reinstalling that package with synaptic first as outlined in a previous message.

Okay, here goes. I'll post the results.

---

### Post by sbergman27 on 2006-09-30
> **sbergman27 said:**
> But don't debs contain gzip'd archives?  i.e. isn't it guaranteed that if he uninstalls the gzip package he won't be able to get it, or anything else to install, period?

Just for kicks, I backed up gzip/gunzip and tried this on my laptop.  It seems that dpkg has its own gzip/gunzip functions built in.  So I was, indeed, able to reinstall the gzip package after removing it.

---

### Post by Carbonfish on 2006-09-30
Hi Steve,

Sorry about the absence, but my system is borked and I had to race home to get my Mac so that I could get back on line.

I tried to remove the libgtkmm-2.4-1c2a package and when I opened Synaptic and searched for the file my system froze and I had to force quit. Then I restarted and opened Firefox to get back to you and the system froze again and the HDD started reading or writing wildly and I had to hold the power button down to force the system down.

I never had a chance to remove the libgtkmm-2.4-1c2a package, or even get close to dealing with the gzip package.

The only thing I can think of to do at this point is to boot to a terminal (or console) and try to do the removal and then update/upgrade from there without starting Gnome, but I will need help with that.

Let me know what you think. After you reply I will have to go back to where the open net is in case as no matter what, I will have to connect the Linux box (the ThinkPad) to do the upgrade.

I'll wait to hear back from you. Thanks again for taking the time to help me with this problem. I know how frustrating it is to sit and wait for a reply on a BB, so I really appreciate your help.

Kent

---

### Post by sbergman27 on 2006-09-30
> **Carbonfish said:**
> Hi Steve,

Sorry about the absence, 

You can ctrl-alt-f1 to get to a text console.

Log in. 

Then "sudo -s" and give your password.

You'll get a "#" prompt meaning you are root, so you don't have to use sudo for everything.

Then:

dpkg -P --force-depends libgtkmm-2.4-1c2a
apt-get install libgtkmm-2.4-1c2a

---

### Post by sbergman27 on 2006-09-30
By the way, at the graphical login screen you can select Options->Select Session->Failsafe Terminal.

Then log in.  You'll just get a screen with a terminal.

In the terminal, type:

```
metacity &
firefox &
```

And you'll be in firefox without gnome.  After you exit firefox, you can close the terminal and it will automatically log you out.

---

### Post by picpak on 2006-09-30
Didn't know apt had its own gzip. For a second I was going to think of extracting the deb and manually copying the files.

Here's hoping the failsafe terminal works for you.

---

### Post by sbergman27 on 2006-09-30
> **picpak said:**
> Here's hoping the failsafe terminal works for you.

Any ideas on the Gnome desktop problem?  Sounds like a lot of swapping is going on when he tries to open a sizable program.  Low memory and the swap didn't get mounted for some reason?

---

### Post by Carbonfish on 2006-09-30
Hi guys,

I am typing this from the Mac, but I have a terminal up on the ThinkPad and am going to try to remove and replace the the gzip package and then upgrade from there. I will use picpak's suggested code and go from there.

KC

---

### Post by Carbonfish on 2006-09-30
Okay, Tried picpak's method and got this... same deal.:( 

carbonfish@carbonfish-laptop:~$ sudo dpkg -P --force-depends libgtkmm-2.4-1c2a gzip
Password:
dpkg: error processing gzip (--purge):
 This is an essential package - it should not be removed.
dpkg: libgtkmm-2.4-1c2a: dependency problems, but removing anyway as you request:
 libglademm-2.4-1c2a depends on libgtkmm-2.4-1c2a.
 sysinfo depends on libgtkmm-2.4-1c2a.
(Reading database ... dpkg: error processing libgtkmm-2.4-1c2a (--purge):
 failed in buffer_read(fd): files list for package `libgtkmm-2.4-1c2a': Invalid argument
Errors were encountered while processing:
 gzip
 libgtkmm-2.4-1c2a
Processing was halted because there were too many errors.
carbonfish@carbonfish-laptop:~$

Next I tried to remove just libgtkmm-2.4-1c2a and this is what I got:

carbonfish@carbonfish-laptop:~$ sudo dpkg -P --force-depends libgtkmm-2.4-1c2a gzip
Password:
dpkg: error processing gzip (--purge):
 This is an essential package - it should not be removed.
dpkg: libgtkmm-2.4-1c2a: dependency problems, but removing anyway as you request:
 libglademm-2.4-1c2a depends on libgtkmm-2.4-1c2a.
 sysinfo depends on libgtkmm-2.4-1c2a.
(Reading database ... dpkg: error processing libgtkmm-2.4-1c2a (--purge):
 failed in buffer_read(fd): files list for package `libgtkmm-2.4-1c2a': Invalid argument
Errors were encountered while processing:
 gzip
 libgtkmm-2.4-1c2a
Processing was halted because there were too many errors.
carbonfish@carbonfish-laptop:~$ sudo apt-get remove libgtkmm-2.4-1c2a
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  libglademm-2.4-1c2a libgtkmm-2.4-1c2a sysinfo
0 upgraded, 0 newly installed, 3 to remove and 24 not upgraded.
Need to get 0B of archives.
After unpacking, 3977kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing sysinfo (--remove):
 failed in buffer_read(fd): files list for package `libgtkmm-2.4-1c2a': Invalid argument
Errors were encountered while processing:
 sysinfo
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
carbonfish@carbonfish-laptop:~$

As far as I can tell **everything** is failing in the buffer_read(fd).

I don't know what the hell is going on. I brought the Ubuntu install disk, but I *really* don't want to start from scratch.

KC

---

### Post by sbergman27 on 2006-09-30
Well, I'm running out of ideas.

I suspect that your dpkg dababase is corrupt.

It lives in /var/lib/dpkg.

There is a script I found on the debian site that is supposed to rebuild it.  I have *no* experience with it.  But it may be worth a try.

[http://www.debian.org/doc/manuals/reference/examples/debian-package-database-rebuild](http://www.debian.org/doc/manuals/reference/examples/debian-package-database-rebuild)

I'm getting ready to reinstall on my laptop for some benchmarking anyway.  I'll test it and see what it does.

---

### Post by Carbonfish on 2006-09-30
I found this thread:  [http://www.ubuntuforums.org/showthread.php?t=192792](http://www.ubuntuforums.org/showthread.php?t=192792)

But it doesn't seem to offer any fixes we haven't already tried.

Did you guys bail on me???

---

### Post by Carbonfish on 2006-09-30
Hi Steve,

I didn't see your post until just now as we posted at the same time and I didn't refresh the page.

Can I just copy and paste that script into a terminal? Sorry about needing so much hand-holding, but I have only been using Linux for a little over a month and am learning as fast as I can.

Thanks again for sticking with me.

Kent

---

### Post by sbergman27 on 2006-09-30
Well, that script won't even run.  Syntax errors.

How about this:

sudo -s
mv /var/lib/dpkg/info/gzip* ~/
mv /var/lib/dpkg/info/libgtkmm* ~/
apt-get -f install
dpkg -P --force-depends gzip 
dpkg -P --force-depends libgtkmm-2.4-1c2a 
sudo apt-get install gzip
sudo apt-get install libgtkmm-2.4-1c2a

---

### Post by Carbonfish on 2006-09-30
Okay Steve,

Ran your code and got this:

carbonfish@carbonfish-laptop:~$ sudo apt-get remove gzip_1.3.5-12ubuntu0.1_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gzip_1.3.5-12ubuntu0.1_i386.deb
carbonfish@carbonfish-laptop:~$ sudo apt-get install gzip_1.3.5-12ubuntu0.1_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gzip_1.3.5-12ubuntu0.1_i386.deb
carbonfish@carbonfish-laptop:~$ sudo -s
root@carbonfish-laptop:~# mv /var/lib/dpkg/info/gzip* ~/
root@carbonfish-laptop:~# mv /var/lib/dpkg/info/libgtkmm* ~/
root@carbonfish-laptop:~# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
root@carbonfish-laptop:~# dpkg -P --force-depends gzip
dpkg: error processing gzip (--purge):
 This is an essential package - it should not be removed.
Errors were encountered while processing:
 gzip
root@carbonfish-laptop:~# dpkg -P --force-depends libgtkmm-2.4-1c2a
dpkg: libgtkmm-2.4-1c2a: dependency problems, but removing anyway as you request:
 libglademm-2.4-1c2a depends on libgtkmm-2.4-1c2a.
 sysinfo depends on libgtkmm-2.4-1c2a.
(Reading database ...
dpkg: serious warning: files list file for package `libgtkmm-2.4-1c2a' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gzip' missing, assuming package has no files currently installed.
79412 files and directories currently installed.)
Removing libgtkmm-2.4-1c2a ...
root@carbonfish-laptop:~# sudo apt-get install gzip
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libglademm-2.4-1c2a: Depends: libgtkmm-2.4-1c2a but it is not going to be installed
  sysinfo: Depends: libgtkmm-2.4-1c2a but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@carbonfish-laptop:~# sudo apt-get install libgtkmm-2.4-1c2a
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libgtkmm-2.4-1c2a
0 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
Need to get 915kB of archives.
After unpacking, 3363kB of additional disk space will be used.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main libgtkmm-2.4-1c2a 1:2.8.8-0ubuntu1
  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gtkmm2.4/libgtkmm-2.4-1c2a_2.8.8-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtkmm2.4/libgtkmm-2.4-1c2a_2.8.8-0ubuntu1_i386.deb) 404 Not Found
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.
root@carbonfish-laptop:~#
root@carbonfish-laptop:~# sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
  404 Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz) 404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@carbonfish-laptop:~#

I don't know what that did. Should I re-boot and try upgrade again?

---

### Post by sbergman27 on 2006-09-30
Not sure, but it actually looks a bit promising.

What does 'apt-get update' do now?

---

### Post by Carbonfish on 2006-09-30
Looking at this, I wonder if this network is behind a firewall and I'm not getting through to the repositories?

This is frustrating. I don't want to have to find another open net to try.

KC

---

### Post by sbergman27 on 2006-09-30
Well, on the removes and installs, you should not give the full filename.

Just 'gzip' and 'libgtkmm-2.4-1c2a'.

It wants the package name and not the name of the deb file.  That's why you get the not found errors, I think.

---

### Post by Carbonfish on 2006-09-30
Steve, 

Here is what I got from the update/upgrade. I think we might be making progress! :p 


carbonfish@carbonfish-laptop:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Fetched 581B in 12s (48B/s)
Reading package lists... Done
carbonfish@carbonfish-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libglademm-2.4-1c2a: Depends: libgtkmm-2.4-1c2a but it is not installed
  sysinfo: Depends: libgtkmm-2.4-1c2a but it is not installed
E: Unmet dependencies. Try using -f.
carbonfish@carbonfish-laptop:~$


KC

---

### Post by sbergman27 on 2006-09-30
sudo apt-get -f upgrade

---

### Post by Carbonfish on 2006-09-30
It's running!! I think it's working! I'll post results when it finishes.

KC

---

### Post by Carbonfish on 2006-09-30
Steve! **You are a fu@#$ng GOD ! ! !** The system is re-booting right now, and of course now is the time that the auto fsck would have to happen, so I have to wait, but I think everything is fixed!!

Thanks man!! Thank you 

Oh oh! The fsck failed. I am running it manually right now.

---

### Post by sbergman27 on 2006-09-30
OK. The next thing is to figure out what's going on when you bring up the full desktop and go into firefox or whatever.

What are the results if you just type:

free

in a terminal?

---

### Post by Carbonfish on 2006-09-30
> **sbergman27 said:**
> OK. The next thing is to figure out what's going on when you bring up the full desktop and go into firefox or whatever.

What are the results if you just type:

free

in a terminal?

Here you go:

carbonfish@carbonfish-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:        255672     251636       4036          0       6428     131880
-/+ buffers/cache:     113328     142344
Swap:       746980          0     746980
carbonfish@carbonfish-laptop:~$

Right now I am using the desktop/Firefox, etc. So things are working!

---

### Post by sbergman27 on 2006-09-30
OK.  I was wondering if maybe your swap wasn't getting mounted, but it looks OK.

So, we had a bad file in the dpkg database for either gzip or the libgtkmm-2.4-1c2a package.

Sounds like you're set then! :-)

---

### Post by bulldog on 2006-09-30
Congrats,guy's!

Wasn't of much help in this but I hope it's solved.

Nice work.

---

### Post by Carbonfish on 2006-09-30
> **sbergman27 said:**
> OK.  I was wondering if maybe your swap wasn't getting mounted, but it looks OK.

So, we had a bad file in the dpkg database for either gzip or the libgtkmm-2.4-1c2apackage.

Sounds like you're set then! :-)

Steve,

I can't begin to tell you how grateful I am. It is this kind of community involvement that makes using Ubuntu gratifying regardless of the actual strengths or shortcomings of the OS. 

You have helped me learn so much more than if I had just given up and re-installed the OS from the live CD, and you have saved me the trouble of setting up everything all over again that I had gotten just the way I like it.

You sir, are a tribute to Linux and the Ubuntu community!

Long may you wave!

I also want to say a sincere "Thank you" to bulldog and picpak and everyone else who helped for their input and assistance!! Thanks guys.. Really!

Kent

---

### Post by sbergman27 on 2006-09-30
> **Carbonfish said:**
> It is this kind of community involvement that make using Ubuntu gratifying regardless of the actual strengths or shortcomings of the OS.

You've really hit on something, there.

I've been working with computers since 1978, with Unix since 1988, and Linux since 1996.  I've interacted with the communities surrounding a number of different Unix versions and Linux distros.  I've been a loyal user of RedHat and derivatives for many years.  And it is the Ubuntu *community*, even more than the distro itself (which is quite good) that won me over.

For years, when new users would ask me what Linux distro they should use, I didn't have a good answer.  Anything I recommended felt a bit like feeding them to the lions because of the RTFM culture that has always permeated the Unix world.

But now, I do not hesitate to recommend Ubuntu.  I give them the URL for Ubuntu Forums and an installation CD, and I know that they will be well taken care of, without actually being my *responsibility*.

---

