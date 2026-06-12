---
title: "Amarok won't install"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by This One Kid on 2008-02-29
This is what I get when I try to install Amarok.


```
-Desktop:~$ sudo apt-get install amarok
```

This is the error I'm getting.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: python-qt3 but it is not going to be installed
E: Broken packages
```

Help?

---

### Post by igknighted on 2008-02-29
> **This One Kid said:**
> This is what I get when I try to install Amarok.


```
-Desktop:~$ sudo apt-get install amarok
```

This is the error I'm getting.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  amarok: Depends: python-qt3 but it is not going to be installed
E: Broken packages
```

Help?

What version of Ubuntu are you using?  Also, can you post the results of the command 'cat /etc/apt/sources.list'?

---

### Post by This One Kid on 2008-02-29
```
-Desktop:~$ cat /etc/apt/sources.list
```


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
deb http://packages.medibuntu.org/ dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.canonical.com/ubuntu dapper-commercial main
```


And I'm using Ubuntu 7.10 - Gusty Gibbon

---

### Post by This One Kid on 2008-02-29
Anyone know whats up?

---

### Post by zvacet on 2008-03-01
You need to add extra repositories like [here](https://help.ubuntu.com/community/Repositories/Ubuntu) or you can change your source list
following [this.](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)After that you will have Amarok in synaptic.

---

### Post by Martje_001 on 2008-03-01
Do this:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo apt-get install amarok
```

---

