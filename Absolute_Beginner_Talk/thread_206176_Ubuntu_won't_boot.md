---
title: "Ubuntu won't boot"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by lonegranger on 2006-06-29
Help please,
                 I've been running Ubuntu for a month or so now. Upgraded ok from badger to dapper and all seemed ok. I use grub to dual boot into Linux or XP. Linux is on it's own drive as master on IDE1 with XP as master on IDE2. Now for some reason when I have both drives connected I get the error message "NTLDR is missing"  and the system halts. When I disconnect the Linux drive on IDE1 it boots straight into XP no problem. Any ideas how I can get back to Linux.

Thanks

---

### Post by ovimunt on 2006-06-29
Can you boot linux if you disconect the XP drive, IDE2 ?

---

### Post by wpshooter on 2006-06-29
Sorry, I have no idea how you would fix, but things like this are why I would never have two O/Ss on the same computer, but to each his own !!!  

And hopefully, fairly soon, I am going to have just one in the house, Ubuntu.

Good luck.

---

### Post by lonegranger on 2006-06-29
No the Linux drive won't boot on it's own

---

### Post by ovimunt on 2006-06-29
Well, it looks to me like the MBR on you Ubuntu drive has been messed up by Windows. 

"NTLDR is missing" is a Windows error. [http://www.computerhope.com/issues/ch000465.htm]("http://www.computerhope.com/issues/ch000465.htm")

First thing you can try is to reinstall GRUB on your IDE1 while IDE2 is connected. To find out how to reinstall GRUB have a look here:

[http://ubuntuos.com/2006/03/howto-restore-grub]("http://ubuntuos.com/2006/03/howto-restore-grub")

---

### Post by ovimunt on 2006-06-29
Oh, and let me know if you fixed it.

---

### Post by lonegranger on 2006-06-29
Thanks for the info. I'll give it a try.

---

