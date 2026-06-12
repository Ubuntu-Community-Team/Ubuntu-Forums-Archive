---
title: "Help with wireless connection"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by naknak987 on 2007-08-09
My neighbors gave me permission to connect to their wireless network. But I cant figure out how to connect to it. I tryed to use the help documents that are on the ubuntu website. I didn't get far tho, I got confused. I think that the card itself is disabled, but not shure. My card is a built in Broadcom 4306. If I cant get this working, then I'll have to install windows again. :(  Any help is apritiated.

---

### Post by anewguy on 2007-08-09
There is no built-in driver that will work with the Broadcom 43xx series.  Many posts have been made on this forum as well as in the tips and tricks forum.  Basically, you have to have the Windows version of the bcmwl5a.inf file and the bcmwl5.sys file.  Then you use ndiswrapper to install them.  There is another option which is to install the firmware cutter package and use it to get the card working.  Both of these are explained on this and other forums many many times.  So, if you don't mind, I going to redirect you to a how-to for my laptop.  If you read it you'll see what is needed to get your Broadcom card working.  Worry not that yours is a 06 and mine is a 18.  Just follow this post:

[http://ubuntuforums.org/showthread.php?t=507505]("http://ubuntuforums.org/showthread.php?t=507505")

You should be able to download and use the Gateway driver, as it is all Broadcom 43xx stuff anyway.  Please also note the section in the wireless portion that tells you how to edit the blacklist file and then reboot.:)

---

### Post by naknak987 on 2007-08-12
Thank you, that worked.

---

