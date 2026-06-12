---
title: "Cannot install 'audacity'"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by dorogavtsev on 2007-10-22
> Cannot install 'audacity'

This application conflicts with other installed software. To install 'audacity' the conflicting software must be removed first.

what should I do? thxs :-)

---

### Post by realvz on 2007-10-22
try audacious

sudo apt-get install audacious

---

### Post by dorogavtsev on 2007-10-22
> nikita@nikita-laptop:~$ sudo apt-get install audacious
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
  audacious: Depends: audacious-plugins (>= 1.3) but it is not going to be installed
             Depends: audacious-plugins (< 1.4) but it is not going to be installed
E: Broken packages


:-(

---

### Post by realvz on 2007-10-22
are you running gutsy or fiesty?
check all you repos are selected properly.

also try running 
sudo apt-get update
sudo apt-get upgrade
and then try to install it again

---

### Post by dorogavtsev on 2007-10-22
> **realvz said:**
> are you running gutsy or fiesty?
check all you repos are selected properly.

also try running 
sudo apt-get update
sudo apt-get upgrade
and then try to install it again

Gutsy...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

still cannot install... :-(

---

### Post by realvz on 2007-10-22
can you post your /etc/apt/sources.list file

---

