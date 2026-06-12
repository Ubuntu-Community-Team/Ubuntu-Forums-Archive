---
title: "Ubuntu on Dell Latitude L100"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Fireborn on 2006-07-04
I've tried with the live CD, to connect to the internet using the wireless addapter built in. it is a Dell Wireless WLAN 1350 cardamajig. I can't get the OS to detect it. It shows activity and such, though I have no connectivity. I don't even know how to check to see what wireless adapters are avalible for use. ALso the X serer dosn't seem tow ant to work. I think I just might ahve to not use Ubuntu for my laptop.

---

### Post by givré on 2006-07-04
Your dell wireless card use the broadcom chipset. This chipset, is not detected out-of-the box in linux, but you could use ndiswrapper to install windows'one : [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Also you can have a look there [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)
I'm not a specialist, so i can't confirm it will work for you, you have to be sure of the version of your broadcom chipset first.

EDIT: for your X problem, what is your graphic card?

---

### Post by givré on 2006-07-04
An other interesting thread [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

