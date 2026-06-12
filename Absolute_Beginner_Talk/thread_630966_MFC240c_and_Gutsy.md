---
title: "MFC240c and Gutsy"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by McNee on 2007-12-03
I have a Brother MFC240c. I like it...
Ever since switching from WinXP to Ubuntu I've been trying to get this printer to work.

Right now, my Update Manager says it needs to update, but when it opens, I get 

> A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package mfc240ccupswrapper needs to be reinstalled, but I can't find an archive for it.

I've tried the different stuff from 
[http://ubuntuforums.org/showthread.php?t=423461]("http://ubuntuforums.org/showthread.php?t=423461")
and the latest I tried was trying to remove the cupswrapper so I could maybe start over...

I tried -  
sudo dpkg --remove --force-all mfc240ccupswrapper

and got...
> dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 89000 files and directories currently installed.)
Removing mfc240ccupswrapper ...
/var/lib/dpkg/info/mfc240ccupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
dpkg: error processing mfc240ccupswrapper (--remove):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc240ccupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc240c/cupswrapper/cupswrappermfc240c: not found
cp: cannot stat `/usr/share/cups/model/brmfc240c.ppd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mfc240ccupswrapper
panther@panther-desktop:~$ 

still have the update manager error... 

I get the printer icon on the system toolbar, it says no documents queued
the printer shows up when I go to System - Administration - Printers
the printer shows up, Try to print a test page - nothing gets queued, nothing prints....

I am... at a loss.

Anyone?

---

