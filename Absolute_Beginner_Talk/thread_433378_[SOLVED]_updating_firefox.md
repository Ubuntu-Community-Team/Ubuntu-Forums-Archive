---
title: "[SOLVED] updating firefox"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by mike g on 2007-05-04
Trying to update to firefox 2 from 1.5.  I am using 6.6.  I can get the extract to work to a temp file but can not get it to update firefox.  In fact I cant seem to get it to do anything.

Any suggestions?

Mike

---

### Post by Acglaphotis on 2007-05-04
```
sudo file-roller
```

Extract firefox 2 to /opt, then run firefox from there.

-Acgla

---

### Post by Sef on 2007-05-04
Enable the backports in Dapper's sources list.

Open the terminal (Applications > Accessories > Terminal):

Uncomment the backport lines (remove the # before those lines.)

---

### Post by confused57 on 2007-05-04
This is the easiest way to install the new firefox:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox)

---

