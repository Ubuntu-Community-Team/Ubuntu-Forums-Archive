---
title: "Win XP cant see U7 Server files"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by pw_jim on 2007-11-12
I am running an XP SP2 machine and Ubuntu Server 7 on a LAN behind a firewall.

I am able to read and write files on the XP (shared folder) from the Ubuntu Server.

I am Not able to read and write files on the Ubuntu Server (shared folder) from the XP.
I set the Ubuntu Server shared folder permissions to 777.
I can PING both ways.

The folder  "open"  is the one I can't see from the  XP PC.

I tried a   "chown"   to change the owner/user to musers/users. Didn't work.



I would appreciate a little help at this point.


Thanks in advance,

   jim





The following info may help.





 
william@U7Server:/home$ ls -al
total 28
drwxr-xr-x  7 root    root    4096 2007-11-12 11:20 .
drwxr-xr-x 21 root    root    4096 2007-11-07 13:46 ..
drwxr-xr-x  2 jim     users   4096 2007-11-12 11:20 jim
drwxrwxrwx  3 root    root    4096 2007-11-12 16:54 open
drwxr-xr-x 31 william william 4096 2007-11-12 17:00 william
william@U7Server:/home$ 





RE: Ubuntu Server 7
LLAMP & Postgress
GNOME GDE



PC Description:
Dell Dimension L866r - P3
866 Mhz
512 Mb RAM
8 Gb HD

---

### Post by jken146 on 2007-11-17
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

