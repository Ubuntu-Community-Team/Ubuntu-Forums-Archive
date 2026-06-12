---
title: "where is my executable file"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-05-08
Here is what I did:

> mozkaynak@ozkaynak:~/setup files$ sudo dpkg -i icaclient_10.0-2_i386.deb 
Selecting previously deselected package icaclient.
(Reading database ... 106041 files and directories currently installed.)
Unpacking icaclient (from icaclient_10.0-2_i386.deb) ...
Setting up icaclient (10.0-2) ...


Then I assume icaclient executable file should be in either /bin or /usr/bin or /usr/sbin or ~/bin
right? but it is no in any of those directories.
Any idea?
Thanks

---

### Post by taurus on 2007-05-08
```
whereis icaclient
or
locate icaclient
```

---

