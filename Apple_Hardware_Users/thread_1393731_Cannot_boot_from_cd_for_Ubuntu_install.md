---
title: "Cannot boot from cd for Ubuntu install"
date: 2010-01-29
forum: Apple Hardware Users
---

### Post by desertrat19 on 2010-01-29
I am trying to put ubuntu an old imac with osx that a former customer gave me. I am not extremely well versed in Apple products but have been doing research into my current problem. I have tried just putting in the ubuntu shipit disc I have, along with downloading and burning 9.10 text based and have not been able to get it to install. I have tried holding 'c' when rebooting, holding 'option' while rebooting (it only gives me the choice of booting from osx), and holding 'control, option, apple, delete' as well to no avail. I then tried downloading Virtualbox and mounting the dmg and found out that my imac is not letting me mount any dmg's at all. Any guidance? Can I take out the harddrive and hook it as a slave to my pc and somehow install ubuntu that way and put it back in the imac? All I want is for the imac to be useful again as I was trying to make it into a stand alone dvd player. Any help would be appreciated.

---

### Post by LtPitt on 2010-01-29
Check faq :)

---

### Post by linuxopjemac on 2010-01-30
Check first if your version of Ubuntu is PPC based.
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by jbiggs12 on 2010-01-31
Is the ubuntu image a .dmg or a .iso? Last I checked, VirtualBox in Mac won't let you mount a .dmg file. And I'm pretty sure that the file system/boot records, etc between a .dmg and a .iso are completely different, so you might try burning a new disk using a .iso image. Good luck!

---

### Post by yokohama1970 on 2010-02-01
I downloaded the iso image for Power PC Ubuntu 8.04 & used Disk Utility in 10.5.8 (leopard) to burn the image to CD-R. It will let you try the Live CD & if that is working, proceed to install Ubuntu 8.04 LTS.

Ubuntu 8.04 PowerPC LiveCd will not boot on iBookG4
Hold down 'c' to boot the cd. At the livecd prompt (which is yaboot), type the following

live-nosplash-powerpc modprobe ide-core video=radeonfb:1024x768-24@60

Have patience because it should take a while to boot.

[https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu%208.04%20PowerPC%20LiveCd%20will%20not%20boot%20on%20iBookG4]("https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu%208.04%20PowerPC%20LiveCd%20will%20not%20boot%20on%20iBookG4")

a1106 2gb Ram SuperDrive OS X 10.5.8
a1046 1.5gb Ram SuperDrive Ubuntu 8.04

---

