---
title: "Another HOWTO DELL Inspiron wireless Broadcom"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2007-11-11
[This]("http://ubuntuforums.org/showthread.php?t=297092&highlight=HOWTO+dell+inspiron") is the original HOWTO. I am just adding something which I think most newbies like me forget to do (actually don't know that they have to do it). After you've done what the HOWTO says type:

sudo iwlist scanning

it should get a list of the networks available with all details. If you are using 6.10 or earlier version (not sure about 7.04) you should click on System>Administration>Network and in the Wireless network add the details with the password as ASCII (in most cases). Then from the upper panel click on the 2 small computers that show your connection status and choose ethx instead if lo where x is a number ( the number that was shown next to your network when you typed sudo iwlist scanning (but anyway if you are using just one wireless network you should have just one ethx so doesn't matter). You should get everything working now. And DON'T delete  the folders where you extracted ndiswrapper or the R151517. You can move them though.

Many 10x to the person that wrote the [HOWTO]("http://ubuntuforums.org/showthread.php?t=297092&highlight=HOWTO+dell+inspiron")

---

