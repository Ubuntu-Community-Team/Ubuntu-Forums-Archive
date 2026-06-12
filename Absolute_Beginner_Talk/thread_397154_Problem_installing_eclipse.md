---
title: "Problem installing eclipse"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2007-03-30
Hello.

I want to install Eclipse on my ubuntu 6.10 box.

However, when I run the command to install, I get the following error messages:


ahlandberg@ubuntu610:~$ sudo aptitude install eclipse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find package "eclipse". However, the following
packages contain "eclipse" in their name:
  eclipse-ecj eclipse-efj eclipse-jdt-gcj eclipse-source eclipse-jdt 
  eclipse-rcp-common eclipse-pde eclipse-platform-common eclipse-rcp 
  eclipse-sdk eclipse-base eclipse-ecj-gcj eclipse-pde-gcj 
  eclipse-platform-gcj eclipse-nls-sdk eclipse-pde-common eclipse-platform 
  eclipse-jdt-common eclipse-rcp-gcj 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.



My /etc/apt/sources.list file contains:


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




I copied the contents from the example sources.list file from the Ubuntu Edgy Guide website. I have the feeling that I need to add some sources so that I actually can install more things. I also have problems installing an SSH Server. It gives me similar problems as described above.

Thanks in advance!!

Anders

---

### Post by undertherift on 2007-03-30
When you're typing apt-get install xxx you  have to match it exactly. ( aptitude install eclipse-gcj )

I say, go through Synpatic GUI, and search for eclipse.  Then you can check off and install what you need, and it'll give you more recommendations.

OpenSSH is the ssh you're looking for; do it the same way.

---

### Post by haelters on 2007-03-30
in your sources.list you are using settings for breezy, but you should use the edgy settings:
```

deb http://be.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

```

---

### Post by igknighted on 2007-03-30
I believe the package you want is eclipse-platform.

EDIT: Woah, yeah.  Your sources all say Breezy, are you sure you don't have 5.10 installed?

---

