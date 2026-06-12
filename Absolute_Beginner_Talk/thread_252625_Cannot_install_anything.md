---
title: "Cannot install anything"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Proshka on 2006-09-07
Hi there,

I do not know what happened to my Ubuntu 6.0.6, which was working absolutely fine, but now I cannot install anything from any source (Cd, repositories, etc.). Once the updates or the applications are dowloaded, I always have a message saying, for example,

E: /var/cache/apt/archives/openssl_0.9.8a-7ubuntu0.1_i386.deb: el subproceso rm cleanup devolvió el código de salida de error 2

which is Spanish for "the rm cleanup subprocess returned the output error code 2". This applies to every single update or installation I want to do and it always refers to /var/cache/apt/archives/. 
Can you please help me?

---

### Post by bluefrog on 2006-09-07
try
sudo apt-get clean   (it flushes the deb cache)

and then try again to install stuff

James

---

### Post by Proshka on 2006-09-07
Hi James,

Thanks for your message. Unfortunately the problem is still there. 

Proshka

---

### Post by tatimmer on 2006-09-07
Whe I have problems with Synaptic, I resort to the command line.  Edit your /etc/apt/sources.list with the following and then run "sudo apt-get update".  If you dont want to use BACKPORT or PLF just put # in front.  After doing this Synaptic should behave, or just get used to using the commandline.



## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free 

***************************************************

some misc apt-get commands:
<apt-cache search notsureofpackagename> 
<apt-get update> sources list
<apt-get install packagename>
<apt-get remove packagename>
<apt-get upgrade> all installed packages
<apt-get dist-upgrade>
<dpkg -l *package-name-pattern*> List installed packages matching pattern
<apt-cache showpkg packagename> list package info
<dpkg -S filename>  Which installed package owns the file?
<dpkg -L package> List files in the package
<apt-get autoclean> Run periodically to clean out .deb archives

---

### Post by Proshka on 2006-09-07
I opted by the last resort and reinstalled Ubuntu. Everything works fine again and even better. Thanks for your posting;)

---

