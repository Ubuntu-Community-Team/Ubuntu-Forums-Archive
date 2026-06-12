---
title: "cannot install any new software"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Jerome420 on 2007-12-15
every time that i try to install new software the system tells me that it conflicts with another program and that i need to go to the synaptic package manager to resolve the issue.  this includes any media players, programs, and even wine when i tried to install.  any advice would help.  thanks.

---

### Post by fbmx24 on 2007-12-15
So your not using synaptic to install the software? How are you trying to install the stuff? Let me know and I can try to help out.

---

### Post by Ub1476 on 2007-12-15
Post the output of

```
sudo apt-get install wine
``` (or any other program).

---

### Post by Pumalite on 2007-12-15
Post the output of:
sudo apt-get update
sudo apt-get upgrade

Also:
cat /etc/apt/sources.list

---

### Post by Jerome420 on 2007-12-15
output of sudo apt-get upgrade

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://lu.archive.ubuntu.com](http://lu.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://lu.archive.ubuntu.com](http://lu.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://lu.archive.ubuntu.com](http://lu.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Hit [http://lu.archive.ubuntu.com](http://lu.archive.ubuntu.com) gutsy-updates Release
Hit [http://lu.archive.ubuntu.com](http://lu.archive.ubuntu.com) gutsy-updates/main Packages
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Hit [http://lu.archive.ubuntu.com](http://lu.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://lu.archive.ubuntu.com](http://lu.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://lu.archive.ubuntu.com](http://lu.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Fetched 2B in 0s (2B/s)  
Reading package lists... Done


output of apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


output of sudo apt-get install wine

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
  wine: Depends: libaudio2 but it is not installable
E: Broken packages


anything that can help...thanks

---

### Post by Ub1476 on 2007-12-15
Try this:

```
sudo apt-get install -f
```

---

### Post by Jerome420 on 2007-12-15
output of sudo apt-get install -f

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Pumalite on 2007-12-15
Try to install again. If it doesn't work, try:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by Jerome420 on 2007-12-15
anytime i try to install anything this is what im getting:

Cannot install 'wine'

This application conflicts with other installed software. To install 'wine' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

it does not matter what program it is just replace the 'wine' with any other name

this is when i use the add/remove under applications

---

### Post by Pumalite on 2007-12-15
sudo dpkg --remove --force-remove-reinstreq wine

---

### Post by Jerome420 on 2007-12-16
sudo dpkg --remove --force-remove-reinstreq wine

will not work because it says that wine is not installed

---

### Post by zvacet on 2007-12-16
```
sudo apt-get install libaudio2
```

and after that try to install wine

---

