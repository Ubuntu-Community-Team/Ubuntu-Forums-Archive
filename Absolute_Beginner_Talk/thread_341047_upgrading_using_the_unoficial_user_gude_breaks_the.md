---
title: "upgrading using the unoficial user gude breaks the system"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by jujukubu07 on 2007-01-18
After I installed Edgy I updated with the unofficial user guide of Edgy 6.10  After doing the upgrade [sudo apt-get upgrade] and rebooting the system I lost the GUI ,Xserver-xorg.
as a newbe I could not fix or find a fix for this problem, the fixes I found did not work.
I had to reinstal Edgy , but when I updated the new installation with the repos that are included in the unofficial user guide Edgy .This update installs two diferent kernels that when rebooting the system does not find the xserver . What I was able to boot from the original or older kernel.
Is there an easy way to updated the system using the unofficial user guide or is better not to use that guide at all.

---

### Post by DougieFresh4U on 2007-01-18
If you are using the terminal to upgrade are you also doing a **sudo apt-get -f install** and then are you **sudo dpkg --configure -a**

---

