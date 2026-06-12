---
title: "Newb issues w/wireless and syslinux"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by soaklord on 2007-08-12
OK, rather than creating forum bloat, I thought I would ask both my questions in a single post.  I have downloaded ubuntu 7.04 and put onto a CD.  I can boot from CD and it works on my Gateway 7510gx amd 64 3700.  However, I can not get the wireless to work.  I have tried multiple troubleshooting efforts, enabling the card in two different areas, etc.  I can not seem to search for networks, rather have to connect directly, so am not sure if the card is even active.  I can see my card when I run a query for it from a command prompt (I know I am using bad terminology, if you would like I can go find exactly the correct command), but nada when connecting.  I am using WEP with a 128bit passphrase.  The card is a broadcom 4318mpg I believe.  The rf info on the bottom of the lappy says 94318mpg.

Newb question part deaux...  My DVD r/w drive burned out a long time ago (pun intended) on my lappy, so I am using an external to boot from CD.  I have been trying like crazy to get syslinux to work so I can boot from a USB instead.  But it won't run.  Doesn't want to run when I am in CD mode for ubuntu, and when I try to run in xp, I get a quick dos popup that disappears before I can even register if there is any information in the popup.  Everything says to install syslinux on your machine, but there is no install exe for XP in the download that I can find and when I go to the win32 window and try to run the exe, I get the above error.  Pardon the newbness, but what am I doing wrong?  The documentation on the syslinux page is less than newbfriendly, so can't seem to find any help there.  Since you guys appear to make up such a phenomenal community, I respectfully request your assistance.

---

### Post by euler_fan on 2007-08-12
Please open the terminal, enter the following, and post the results:

```
 lspci | grep Broadcom\ Corporation
```

---

### Post by soaklord on 2007-08-12
03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by euler_fan on 2007-08-12
Try [this.]("http://ubuntuforums.org/showthread.php?t=197102")

---

