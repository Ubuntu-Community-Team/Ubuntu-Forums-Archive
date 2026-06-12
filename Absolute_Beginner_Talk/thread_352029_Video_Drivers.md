---
title: "Video Drivers"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Daemion_AF on 2007-02-02
I tried running the envy script to install my ATIx1400 graphics card on my dell e1705. This is what it looks like when it runs. Anyone have any idea what im doing wrong?

Please select one of the activities displayed above and press ENTER:

3
rm: cannot remove `*.deb': No such file or directory
Ubuntu Dapper 32bit
Your graphic card has been detected as a ATI Mobility Radeon X1400
Your graphic card is supported by the latest driver
 * Stopping GNOME Display Manager...                                     [ ok ]
sudo: /etc/init.d/kdm: command not found
E: Malformed line 34 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
E: Malformed line 34 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
E: Malformed line 34 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
E: Malformed line 34 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
E: Malformed line 34 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
E: Malformed line 34 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
E: Malformed line 34 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
An installer has been detected
md5new: 5fbd42d666d467a904acbaeb600c1d5a
md5sumold: 5fbd42d666d467a904acbaeb600c1d5a
rm: cannot remove `/usr/src/fglrx-kernel*.deb': No such file or directory
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.33.6...................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/dapper
./packages/Ubuntu/ati-packager.sh: line 56: dpkg-architecture: command not foundError: unsupported architecture:
Removing temporary directory: fglrx-install
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
sudo: module-assistant: command not found
sudo: module-assistant: command not found
sudo: module-assistant: command not found
sudo: module-assistant: command not found
rm: cannot remove `*.deb': No such file or directory
rm: cannot remove `*.changes': No such file or directory
Do you want your xorg.conf to be automatically configured? (y/n) \ "y" is the default answer
y
sudo: aticonfig: command not found
sudo: aticonfig: command not found
Do you want to restart your computer now (Recommended)? (y/n) \ "y" is the default answer
n
Remember to restart your computer manually
Operation Completed

---

### Post by mikewhatever on 2007-02-02
To solve this error:
```
E: Malformed line 34 in source list /etc/apt/sources.list (dist)
``` post your sources list here
> gksudo gedit /etc/apt/sources.list
copy and paste

---

### Post by Daemion_AF on 2007-02-02
As requested, BTW i just noticed my Synaptics is broken once again. I have no idea what happened.

deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/)

---

### Post by mikewhatever on 2007-02-02
It looks good, but I am unsure about the beryl repository. Lets leave it to someone more advanced. What's wrong the Synaptic?

---

### Post by Daemion_AF on 2007-02-02
when opening just the add/remove programs this pops up. 
Failed to check for installed and available applications This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.
And it closes the window.

If i go straight to synaptic from system>administration>synaptic I get this popup
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

After that popup i get this popup
The following problems were found on your system
E: Malformed line 33 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: Malformed line 33 in source list /etc/apt/sources.list (dist)
E: Unable to lock the list directory

---

### Post by mikewhatever on 2007-02-02
Have you tried opening Synaptic while the sources file was open?

---

### Post by Daemion_AF on 2007-02-02
yes with and without it open it has the same errors

---

### Post by Daemion_AF on 2007-02-03
any other suggestions?:confused:

---

### Post by bodhi.zazen on 2007-02-03
The last line of your sources.list (for Beryl)should be:

> deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main

---

