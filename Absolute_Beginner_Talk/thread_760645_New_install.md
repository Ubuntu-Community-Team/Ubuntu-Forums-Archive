---
title: "New install"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by walt99 on 2008-04-20
Ok, I installed Ubuntu 7.10. I ran wubu-cdboot.exe from with in Windows XP (SP2). It created a dual boot system. I can get to the Linux login screen and it is asking for a Username and Password. I did not create a username or password during the install, because I was never asked to. What do I do now?

Thanks
Walt

---

### Post by ACMarina on 2008-04-20
IF you ran wubi, you should have created a username and password before it downloaded the image, I think..

Are you sure you didn't do this when you ran the EXE??


EDIT**
Yeah, check this out from the wubi webpage..
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

Looks like you HAD to put in something.. maybe it would be easiest to just dump and retry, and make sure you write it down..

---

### Post by walt99 on 2008-04-20
Thanks for the very quick reply. I did not get any screen asking for a password. I an going to reinstall it from the boot cd. Thanks again.

---

### Post by ACMarina on 2008-04-20
Here's a guide on the install..

[http://arstechnica.com/news.ars/post/20080224-wubi-arrives-a-look-at-ubuntu-8-04-alpha-5.html](http://arstechnica.com/news.ars/post/20080224-wubi-arrives-a-look-at-ubuntu-8-04-alpha-5.html)

---

### Post by walt99 on 2008-04-24
I'm still having much trouble with the install. I have tried several different install disks and I was final able to get to the step where it acctually starts the install. At the stage when it is coping the files it will get to 51% and fail. The message is that it cannot write to the file system due to a bad disk or bad CD. I know the Cd is good because it worked on a different system and the hard drive is new and I have install WinXP on it before. 

This is an HP Pavilion a305w with a Celeron 2.7 CPU and 250G hd and 1G ram I don't know what the video card is but it is on board.

I am going to use a util to totally wipe the hd and retry the install. Anyone else have any thoughts on this?

(BTW this is Ubuntu 7.10)

---

### Post by bumanie on 2008-04-24
I'd be tempted to run chkdisk on windows and make sure the hard drive is OK, as it's new it should be OK, but nothing is guaranteed - it could've been dropped/thumped around during transit - who knows? Also most hard drive manufacturers have tools available to check hard drives for errors - that is probably a better idea than using chkdisk. You can go to the manufacturer's site and see what tools they have. No experience with wubi, but you could always try a dual boot install.

---

