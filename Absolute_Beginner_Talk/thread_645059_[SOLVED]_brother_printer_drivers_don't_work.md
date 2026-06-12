---
title: "[SOLVED] brother printer drivers don't work"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by planC on 2007-12-19
This printer problem is not going away. I have a' brother dcp115c' and installed the 210c drivers as recommended . Still nothing! Then i uninstalled and reinstalled CUPS to see if that made any difference, but still nothing! The printer icon appears, when i click on it the document window appears, and instantly the doc disappears! The printer setting is default but i don't know where to go from here. I can't send any output 'cos there isn't any.... nothing. Have I done something in the set up as even when trying to set the default printer the screen freezes.

---

### Post by plucky on 2007-12-19
Hiya PlanC,

I have the Brother DCP-120C printer and used this thread to install the drivers for it.According to the Brother linux website,it uses the same drivers as the DCP-115C printer

[http://ubuntuforums.org/showthread.php?t=590793&highlight=mfc210c](http://ubuntuforums.org/showthread.php?t=590793&highlight=mfc210c)

It is quite long but easy enough to follow, and the printer and scanner works.This assumes you are running Gutsy, as there is another Howto in the forums for Fiesty which is slightly different.

Hope this helps

---

### Post by planC on 2007-12-20
Thanks heaps plucky, i will give it a try.

---

### Post by planC on 2007-12-20
Here is the output: 
Reading package lists... Done
Building dependency tree
Reading state information... Done
tcsh is already the newest version.
The following packages were automatically installed and are no longer required:
  libzvbi-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ian@ian-desktop:~$ cd Desktop
ian@ian-desktop:~/Desktop$ sudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.deb
(Reading database ... 103805 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.2-3 (using cupswrapperMFC210C-1.0.2-3.i386.deb) ...
lpadmin: The printer or class was not found.
 * Restarting Common Unix Printing System: cupsd                         [ OK ]
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.2-3) ...
ERROR : Brother LPD filter is not installed.
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
chmod: cannot access `/usr/local/Brother/inf/brMFC210Crc': No such file or directory
chmod: cannot access `/usr/local/Brother/inf': No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ]

ian@ian-desktop:~/Desktop$ sudo dpkg -i --force-all mfc210clpr-1.0.2-1.i386.deb
dpkg: error processing mfc210clpr-1.0.2-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc210clpr-1.0.2-1.i386.deb
ian@ian-desktop:~/Desktop$ cd Desktop
bash: cd: Desktop: No such file or directory
ian@ian-desktop:~/Desktop$ sudo cp /usr/lib/cups/filter/brlpdwrapperMFC210C /usr/lib64/cups/filter
cp: cannot create regular file `/usr/lib64/cups/filter': No such file or directory
ian@ian-desktop:~/Desktop$
Something is wrong with the whole thing cos my screen keeps freezing. What do i do???

---

### Post by plucky on 2007-12-20
PlanC

You need to download the **LPR** driver and install it as specified in step 7.

> dpkg: error processing mfc210clpr-1.0.2-1.i386.deb (--install):
cannot access archive: No such file or directory

I think this means it cannot find the **.deb** file on your Desktop.Once that is installed you can then go back and reinstall the CUPS driver.

Good luck

---

### Post by planC on 2007-12-20
I tried this but there is still something wrong. It says there is no such file....
[sudo] password for ian:
Reading package lists... Done
Building dependency tree
Reading state information... Done
tcsh is already the newest version.
The following packages were automatically installed and are no longer required:
  libzvbi-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ian@ian-desktop:~$ cd Desktop
ian@ian-desktop:~/Desktop$ sudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.deb
(Reading database ... 103805 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.2-3 (using cupswrapperMFC210C-1.0.2-3.i386.deb) ...
lpadmin: The printer or class was not found.
 * Restarting Common Unix Printing System: cupsd                         [ OK ]
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.2-3) ...
ERROR : Brother LPD filter is not installed.
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
chmod: cannot access `/usr/local/Brother/inf/brMFC210Crc': No such file or directory
chmod: cannot access `/usr/local/Brother/inf': No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ]

ian@ian-desktop:~/Desktop$ sudo dpkg -i --force-all mfc210clpr-1.0.2-1.i386.deb
Selecting previously deselected package mfc210clpr.
(Reading database ... 103805 files and directories currently installed.)
Unpacking mfc210clpr (from mfc210clpr-1.0.2-1.i386.deb) ...
Setting up mfc210clpr (1.0.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/MFC210C': No such file or directory
chown: cannot access `/var/spool/lpd/MFC210C': No such file or directory
chgrp: cannot access `/var/spool/lpd/MFC210C': No such file or directory
chmod: cannot access `/var/spool/lpd/MFC210C': No such file or directory

ian@ian-desktop:~/Desktop$ cd Desktop
bash: cd: Desktop: No such file or directory
ian@ian-desktop:~/Desktop$ sudo cp /usr/lib/cups/filter/brlpdwrapperMFC210C /usr/lib64/cups/filter
cp: cannot create regular file `/usr/lib64/cups/filter': No such file or directory
ian@ian-desktop:~/Desktop$
  What am i doing wrong???

---

### Post by planC on 2007-12-20
I tried it a couple of times and it finally worked.... Thank you.

---

### Post by plucky on 2007-12-21
Glad to hear,

Was going to try it on another system but sleep got in the way.
Can you mark the thread as solved,using the thread tools at the top of the page

Merry Xmas

:)

---

