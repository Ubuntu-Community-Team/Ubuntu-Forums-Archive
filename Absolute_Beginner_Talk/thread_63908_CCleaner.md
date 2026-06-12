---
title: "CCleaner"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by cadaver on 2005-09-09
Is there a Linux program like CCleaner for Windows? Or is it unnecessary under Linux?

---

### Post by KingBahamut on 2005-09-09
Largely unessecary. 

However, if youre really paranoid about it you can do a few things 

as root 

apt-get autoclean
apt-get clean

--to clean out unessecary files from the apt cache 

cd /tmp 
rm * 

--to remove tmp files from the system 

fsck -sA

--to do a serialized check of all filesystems and repair if needed


Other than that, no, not nessecary.

---

