---
title: "Help creating a launcher. Need it to open term, issue command &amp; stay open for a few?!"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by Getwild2 on 2006-06-02
I have created a launcher that opens a terminal window and issues the following command, sudo /etc/init.d/vsftpd start and another one that issues the command sudo /etc/init.d/vsftpd stop.

The problem is that the above commands are issued so fast that I cannot see to verify that the server has either started or stopped.  Is there any way to put a delay on the automatic close of the window, or leave the window open?

The above is likened to typing ipconfig in Windoze Run menu and having your IP configuration zip by you so fast that you cant see it.  Rather if you type cmd, then ipconfig, the window stays open.  

What do you guys think?  Is this possible?  ](*,)

---

### Post by skinnygmg on 2006-06-02
look here

[http://tille.xalasys.com/training/bash/index.html](http://tille.xalasys.com/training/bash/index.html)

---

### Post by dabear on 2006-06-02
I guess you could append a "read" that would wait untill the user types any output and pressing enter.

[http://www.ss64.com/bash/read.html](http://www.ss64.com/bash/read.html)

---

