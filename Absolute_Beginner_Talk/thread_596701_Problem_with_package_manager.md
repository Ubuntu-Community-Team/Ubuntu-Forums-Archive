---
title: "Problem with package manager"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by omi291 on 2007-10-29
Whenever I try to install something from the Synaptics package manager, I an constantly prompted to refresh the list of programs, and I can never get anything to install. Also, when i try to install wine, i get this error after typing in: "sudo apt-get install wine" into the terminal:

dominator@Javaid:~$ sudo apt-get install wine
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
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages

---

### Post by Pumalite on 2007-10-29
You can try going to Synaptic>Edit>Fix Broken Packages
Also post the output of:
sudo apt-get update.

---

### Post by omi291 on 2007-10-29
> **Pumalite said:**
> 
Also post the output of:
sudo apt-get update.

dominator@Javaid:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Get:2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Fetched 2B in 0s (3B/s)
Reading package lists... Done

---

### Post by omi291 on 2007-10-29
Also, when i try to install wine again, it says another program is conflicting with other installed software, but i have no idea what is causing the problem

---

### Post by Pumalite on 2007-10-29
If you could find out which program it is; that would be the solution to all your problems because it needs to be purged. Look in /var/lib/dpkg/status.

---

### Post by omi291 on 2007-10-29
I have found the file, but i truly have no idea what to do with it. What do I do from there? You can probably already tell i a linux noob...but i really appreciate the help

---

### Post by Pumalite on 2007-10-30
sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by omi291 on 2007-10-30
Sorry, I didn't word my reply right. I meant i found the file "status"....but is there any way to know what package it is that is preventing me from installing wine?

---

### Post by Pumalite on 2007-10-30
You have to look through the file carefully. Most, will say 'Installed...OK installed'. The one that doesn't is the one.

---

### Post by omi291 on 2007-10-30
I found the package. It's called jfsutils. I am running the command you wrote above, and this is the output i get:

sudo dpkg --remove --force-remove-reinstreq jfsutils
[sudo] password for dominator:
dpkg - warning: ignoring request to remove jfsutils which isn't installed.

EDIT: I have looked through the file and have also found that there are several other packages that have the status: purge ok not-installed

---

### Post by Pumalite on 2007-10-30
You could try this with each one of them:
sudo apt-get remove --purge <packagename>

---

