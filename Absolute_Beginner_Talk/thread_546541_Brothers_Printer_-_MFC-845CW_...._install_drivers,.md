---
title: "Brothers Printer - MFC-845CW .... install drivers, getting errors"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by PeteW on 2007-09-09
Hello,

I am new to Ubuntu and trying to get this OS set-up to print to a shared printer on a XP pro box.
I download the drivers from the Brothers site "mfc845cwlpr-1.0.0-9.i386.deb" as the site states.
Then I tried installing as followes:

luke1027@Server1:~/Desktop$ sudo dpkg -i --force-all mfc845cwlpr-1.0.0-9.i386.deb
Password:
(Reading database ... 93006 files and directories currently installed.)
Preparing to replace mfc845cwlpr 1.0.0-9 (using mfc845cwlpr-1.0.0-9.i386.deb) ...
Unpacking replacement mfc845cwlpr ...
Setting up mfc845cwlpr (1.0.0-9) ...
mkdir: cannot create directory `/var/spool/lpd/mfc845cw': No such file or directory
chown: cannot access `/var/spool/lpd/mfc845cw': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc845cw': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc845cw': No such file or directory


However, I am getting errors as you can see.  What am I doing wrong or missing in the install of these printer drivers?

Thanks,

PeteW.

---

