---
title: "[SOLVED] tar.gz files"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Learn!ng on 2007-08-06
Hello just installed feisty today downloaded opera for linux now i have a tar.gz file... how do i make it happen?

---

### Post by aysiu on 2007-08-06
**Step 1**
Delete the .tar.gz. You don't need it.

**Step 2**
Paste this command in [the Konsole terminal](http://www.psychocats.net/ubuntu/terminal): ```
**wget -c http://get.opera.com/pub/opera/linux/922/final/en/i386/shared/opera_9.22-20070716.6-shared-qt_en_i386.deb && sudo dpkg -i opera_9.22-20070716.6-shared-qt_en_i386.deb**
``` The output should look like this: ```
username@ubuntu:~$ [b]wget -c http://get.opera.com/pub/opera/linux/922/final/en/
i386/shared/opera_9.22-20070716.6-shared-qt_en_i386.deb && sudo dpkg -i opera_9.
22-20070716.6-shared-qt_en_i386.deb[/b]
--20:37:02--  http://get.opera.com/pub/opera/linux/922/final/en/i386/shared/oper
a_9.22-20070716.6-shared-qt_en_i386.deb
           => `opera_9.22-20070716.6-shared-qt_en_i386.deb'
Resolving get.opera.com... 213.236.208.156
Connecting to get.opera.com|213.236.208.156|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5,653,616 (5.4M) [application/x-debian-package]

100%[==============================================================================================================================>] 5,653,616    150.99K/s    ETA 00:00

20:38:28 (65.65 KB/s) - `opera_9.22-20070716.6-shared-qt_en_i386.deb' saved [5653616/5653616]

Password:
Selecting previously deselected package opera.
(Reading database ... 120284 files and directories currently installed.)
Unpacking opera (from opera_9.22-20070716.6-shared-qt_en_i386.deb) ...
Setting up opera (9.22-20070716.6) ...

username@ubuntu:~$ 
```

---

### Post by Learn!ng on 2007-08-06
thanks ;)

---

### Post by aysiu on 2007-08-07
Whenever possible, .deb files are preferable to .tar.gz files for software installation.

---

