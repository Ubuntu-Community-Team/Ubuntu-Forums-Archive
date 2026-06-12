---
title: "Open Office data base; The last step to make a form  will not activate"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by learstar7 on 2007-07-17
I created the table. Then I selected form setup.  I get all the way to step 8 which is "set name". When I click on 
finish nothing happens.  I have redone the complete steps to create a data-base numerous times with the same 
result.  Is there some pre-condition that needs to be satisfied or is there a possibility that I have a problem with 
Open Office Base.  

I am using Ubuntu 7.04  (fiesty fawn)

Thanks     learstar7

---

### Post by dougfractal on 2007-07-17
Unfortunately this is a bug in feisty, (fixed in gusty)
due to ubuntu not compiling it with sun java. 

What i did was:

> One solution to the problem is:
1. Uninstall OO from ubuntu.
2. Find deb package for OO from somewhere
OR
Get the RPM packages from the OO website
Unpack the file
Use alien (in a terminal: alien -i *.rpm) to convert to debs and install
Have fun with a working OO.....

from " [Should Ubuntu have its own Open Office???]("http://ubuntuforums.org/showthread.php?t=316908")"

Running this script will also remove the ubuntu-desktop package. No worry, this is a meta package that can be removed safely. But in case you want to upgrade your whole distro, you'll have to install back this package (and the OOo original version). 

This will download OOo_2.2.1 with sun java runtime
for a different version [ftp://gd.tuwien.ac.at/office/openoffice/stable/](ftp://gd.tuwien.ac.at/office/openoffice/stable/)

mirrors:
[http://distribution.openoffice.org/mirrors/#mirrors](http://distribution.openoffice.org/mirrors/#mirrors)

Install
```

sudo apt-get remove openoffice.org-core openoffice.org-common
sudo apt-get install alien
wget ftp://gd.tuwien.ac.at/office/openoffice/stable/2.2.1/OOo_2.2.1_LinuxIntel_install_wJRE_en-US.tar.gz
tar -xzf OO*.tar.gz
cd OO*/RPMS
sudo alien -i --scripts *.rpm
sudo dpkg -i ./desktop-integration/*debian*.deb
```

Uninstall
```
sudo apt-get remove openoffice.org* 
sudo apt-get install ubuntu-desktop
```


[I]
Updated with Hagar de l'Est's  improvements.[/I]

Happy 00o-ing

---

### Post by Hagar Delest on 2007-07-19
For information, I've made a tutorial here : [[Ubuntu] Installing OOo on Debian and Co.](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759)

Beware, type the *--scripts* option in the alien command, else you can face bugs afterwards.

---

