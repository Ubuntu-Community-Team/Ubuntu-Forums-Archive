---
title: "netatalk with external usb hard disk"
date: 2009-01-16
forum: Apple Hardware Users
---

### Post by samick88 on 2009-01-16
I want to use my WD Mybook as backup device for leopard.
I read the article
[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

Everything works fine if I use my local hard drive.
Once I configure netatalk to use my usb-harddrive, I get a connection failed

my /etc/fstab entry:
```
/dev/sdb4       /media/mybook/backup    ext3 defaults,user,noauto 0     0
```

my /etc/netatalk/AppleVolumes.default
```
/media/mybook/backup TimeMachine allow:myuser cnidscheme:cdb options:usedots,upriv
```

directory settings /media/mybook/backup
```
drwxrwxrwx   5 myuser myuser  4096 2009-01-16 20:23 backup
```


I'm using ubuntu server 8.10

Do you have any idea?
Kind regards

---

### Post by samick88 on 2009-01-18
I'v found the solution. I've uninstalled netatalk from ubuntu 8.10 and followed the tutorial from:
[http://www.zaphu.com/2008/04/29/ubuntu-guide-configure-a-netatalk-file-server-based-on-apple-filing-protocol-afp/](http://www.zaphu.com/2008/04/29/ubuntu-guide-configure-a-netatalk-file-server-based-on-apple-filing-protocol-afp/)

did some modifications from 
[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)


server and time machine is working now.

---

