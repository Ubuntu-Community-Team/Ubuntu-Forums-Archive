---
title: "[SOLVED] Brother MFC-440-CN Printer - Please Help!"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by C-A on 2007-11-24
I am trying to install drivers and set up my Brother MFC-440-CN Printer as a network printer. I have read some posts already where some have got their printer to work and others have not. I have read and tried a lot already. I am currently trying to follow  [these directions]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install6.html") from brother's site and while trying in install mfc440cnlpr-1.0.0-9.i386.deb I get this error:

> carl@box-seven:~/Desktop/brother-temp$ sudo dpkg -i --force-all mfc440cnlpr-1.0.0-9.i386.deb
(Reading database ... 
dpkg: serious warning: files list file for package `mfc440cnlpr' missing, assuming package has no files currently installed.
122648 files and directories currently installed.)
Preparing to replace mfc440cnlpr 1.0.0-9 (using mfc440cnlpr-1.0.0-9.i386.deb) ...
Unpacking replacement mfc440cnlpr ...
Setting up mfc440cnlpr (1.0.0-9) ...
mkdir: cannot create directory `/var/spool/lpd/mfc440cn': No such file or directory
chown: cannot access `/var/spool/lpd/mfc440cn': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc440cn': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc440cn': No such file or directory

My goals are to install the drivers and then be able to print via the network.

Any help would be greatly appreciated!

---

### Post by Shazaam on 2007-11-24
I have a Brother MFC420CN and all I did was download the .debs from Brother to my desktop and double-clicked them. Odd that they want a --force -all  command. My drivers installed (including the scanner/fax drivers) and run perfect. I am running Dapper but Feisty/Gutsy should work the same.
As far as the network part mine is set up as a local printer using usb, non networked.

---

### Post by C-A on 2007-11-24
thanks for the reply
it turns out that  the LPR driver is not need in Gutsy
I realized that in [this helpful how-to post for brother printers]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=590793&highlight=brother+how-to") and then followed [brother's instructions]("http://solutions.brother.com/linux/sol/printer/linux/cups_network.html") for cups network settings and now it works!

---

### Post by Shazaam on 2007-11-24
Glad you got it working. Go ahead and mark the thread solved unless you need more help with your printer.

---

