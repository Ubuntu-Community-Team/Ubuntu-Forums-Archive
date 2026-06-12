---
title: "how to restore dapper,"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by CheeseAndToast on 2006-06-24
Howdy,

I've messed something up within the source.list and not sure how to retore.  What is happening is when reloading in synaptic, after enabling universe/multiverse, i get this error:

[HTML]
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences

The following problems were found on your system:
W: Duplicate sources.list entry cdrom://Ubuntu 6.06 _Dapper Drake_ - Release Candidate i386 (20060525) dapper/main Packages (/var/lib/apt/lists/Ubuntu%206.06%20%5fDapper%20Drake%5f%20-%20Release%20Candidate%20i386%20(20060525)_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 6.06 _Dapper Drake_ - Release Candidate i386 (20060525) dapper/restricted Packages (/var/lib/apt/lists/Ubuntu%206.06%20%5fDapper%20Drake%5f%20-%20Release%20Candidate%20i386%20(20060525)_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com dapper/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com dapper/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)
[/HTML]

I basically want the all programs unistalled, if possible??

Can anyone advise?
Cheers

---

### Post by Winblowz on 2006-06-24
Replace your sources.list with the following (copy and paste)...
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free 

```

---

### Post by CheeseAndToast on 2006-06-25
Thanks for your reply.  Its still telling me i've got duplicates.  what i'm trying to do is install PHPmyadmin.  I've got a sourse list, from the wiki, which let me view the PHPmyadmin package within synaptic, but wouldn't let me install it - said something about. *Unable to install, directory locked?*.  Somthing along thoes lines.  Is there no way to taking off all application, and restoring it to its original state?

---

