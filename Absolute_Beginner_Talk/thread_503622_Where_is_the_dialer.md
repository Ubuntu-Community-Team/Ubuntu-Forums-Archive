---
title: "Where is the dialer?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by resander on 2007-07-18
I have just installed Ubuntu 6.10 (mouse did not work on 7.04, but does on 6.10) and have been touring the menus. 

The Internet submenu shows softphone, email, browser and messenger, but I cannot see a dialer (like the dialers for dial-up networking in Windows). My PC has a Conexant winmodem that is not supported, so cannot try clicking on Firefox etc.


 Where is the dialer? How would I connect and disconnect?

---

### Post by FunkyJack on 2007-07-18
First you have to install drivers

[https://help.ubuntu.com/community/DialupModemHowto/Conexant]("https://help.ubuntu.com/community/DialupModemHowto/Conexant")

For dialing you can use wvdial command in terminal but first you have to configure /etc/wvdial.conf

When you are done you will be limited to 14.4 kbps.
I have a patch that will fix that so tell if you need it.

---

### Post by Bartender on 2007-07-18
Take a look at the wiki
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Also, my attempt to keep it simple
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)
which assumes you have a modem that works.  This complex compiling stuff was too much for me - bought some serial externals.

---

