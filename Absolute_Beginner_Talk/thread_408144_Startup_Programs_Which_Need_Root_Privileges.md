---
title: "Startup Programs Which Need Root Privileges"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by RKCole on 2007-04-13
Hello, everyone.

I am finally over my wireless woes.  I have Edgy and my wireless USB dongle (Cnet CWD-854G Wireless USB Dongle using a RaLink RT73 chipset) up and running with WPa2/PSK+AES.  I have a graphical utility which works with the dongle to establish a connection to my network.

I currently have this utility (named **rutilt** set to start up when I login (via System->Preferences->Sessions->Startup Programs), but when I login to GNOME I receive a request for my password.  Is there some way that I can bypass the request for a password for this program on startup?

I used information from [this post]("http://ubuntuforums.org/showpost.php?p=2131392&postcount=2") to try to fix this, but it was to no avail, unfortunately.

Any suggestions would be greatly appreciated.  

Thanks, everyone.

Take care.

---

### Post by yabbadabbadont on 2007-04-13
If there were a non-GUI version of the program, or if the GUI version took command line parameters without needing X, then you could call it from /etc/rc.local and it would be run with root privileges...  Do you know if such a version of the software exists?

---

### Post by RKCole on 2007-04-13
It is a GTK+ 2 application.  I know I can manipulate some things via the command-line, but it is something which would reside on the system tray.

---

### Post by yabbadabbadont on 2007-04-13
Then messing about with the sudoers file is probably the only way that you will get it to work.  :?

---

### Post by RKCole on 2007-04-13
I have the following entry in /etc/sudoers:
```

bob ALL= NOPASSWD: /usr/bin/rutilt

```

Does this look like the right syntax?  I'm not too familiar with editing /etc/sudoers.

Thanks for the input.

Take care.

---

### Post by yabbadabbadont on 2007-04-13
It looks correct to me.  At least it looks like it matches what taurus posted in the link you provided.

---

### Post by rand76 on 2007-04-13
I was having a similar problem with a startup program until I realized something that was never directly mentioned. Be sure to slap a sudo before the startup programs command in the sessions window. eg. sudo /usr/sbin/g15daemon

Simple but easily overlooked.

---

