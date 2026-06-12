---
title: "Removing amule-common"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by bengar on 2007-04-14
I am trying to remove amule-common because I installed it finding a solution to a non working amule, but, it is a old version and when I tryed to removed it this is what appear.
> bengar@bengar-desktop:~$ sudo apt-get remove amule-common
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  amule-common
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 3244kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 182124 files and directories currently installed.)
Removing amule-common ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/ed2k by amule'
  found `diversion of /usr/bin/ed2k to /usr/bin/ed2k.xmule by amule-utils'
dpkg: error processing amule-common (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 amule-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
bengar@bengar-desktop:~$


Any solution will be appreciated. Thanks you my people

---

### Post by juantovarm on 2007-04-15
Try synaptic, look for amule and and click to uninstall completely, maybe that helps

---

### Post by zvacet on 2007-04-15
juantovarm give you good advice.In the future install and remove packages with aptitude.That way you will always install package and dependencies,and when you remove you will remove package and dependencies.For example
```
sudo aptitude install package_name
```

---

### Post by bengar on 2007-04-15
Thank you for all, this is what I did.
> bengar@bengar-desktop:~$ sudo aptitude remove amule-common
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  amule-common
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 3244kB will be freed.
Writing extended state information... Done
(Reading database ... 181461 files and directories currently installed.)
Removing amule-common ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/ed2k by amule'
  found `diversion of /usr/bin/ed2k to /usr/bin/ed2k.xmule by amule-utils'
dpkg: error processing amule-common (--remove): subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 amule-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

Then I did this
> bengar@bengar-desktop:~$ sudo aptitude install amule-common
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate file for the amule-common package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?

How may I do a manual fix? with alt-f2?

---

### Post by speeves on 2007-04-15
It looks like it may be a bug in the package:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=370421](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=370421)

that is picked up from Debian.  Can you double-check that you have either /usr/bin/ed2k or /usr/bin/ed2k.wrapper installed? If not, then:

sudo apt-get install amule-utils

which should install those files, then try to:

sudo apt-get remove amule-common

once more.  

NOTE: aptitude is only a front-end to apt, so you are fine using whichever you are comfortable with.

---

### Post by bengar on 2007-04-16
> **speeves said:**
> It looks like it may be a bug in the package:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=370421](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=370421)

that is picked up from Debian.  Can you double-check that you have either /usr/bin/ed2k or /usr/bin/ed2k.wrapper installed? If not, then:

sudo apt-get install amule-utils

which should install those files, then try to:

sudo apt-get remove amule-common

once more.  

NOTE: aptitude is only a front-end to apt, so you are fine using whichever you are comfortable with.

Okay, thank you, now the problem is growing because all my update can 't download with this error
> E: amule-common: subprocess post-removal script returned error exit status 2

Trying with thats commands i got this
> bengar@bengar-desktop:~$ sudo apt-get amule-utils
Password:
E: Invalid operation amule-utils


Now let me go to check /usr/bin/ed2k.

---

### Post by justleen on 2007-04-16
the syntax is ```
 sudo apt-get install <package> 
```

---

### Post by bengar on 2007-04-16
Yes, there is the ed2k.xmule-2.0. But looking on Synaptic and finding the  amule-commons, I click on it with the right  mouse click on properties and look in version windows I read a message where say to install a different version from default. I select the default version clicking on it only, then I resolved my problem on that way. I looking on Synaptic on the left corner** Package**, then a press force version, then version that a select before was changet finally  reinstall the amule-commons ubuntu default. And that's all folks.


Thank you everybody, I can't do this with a little help of my friends...

---

### Post by bengar on 2007-04-16
> **justleen said:**
> the syntax is ```
 sudo apt-get install <package> 
```

Justleen, thank you you are right, another mistake by me.

---

