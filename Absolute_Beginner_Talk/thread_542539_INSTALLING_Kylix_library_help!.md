---
title: "INSTALLING Kylix library help!"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-09-04
What am I doing wrong???

[IMG]http://i12.tinypic.com/6b44qqr.png[/IMG]
> john@john-desktop:~$ root
bash: root: command not found
john@john-desktop:~$ su
Password:
root@john-desktop:/home/john# /home/john/Desktop/kylixlibs3-borqt/install.sh
install: cannot stat `libborqt-6.9.0-qt2.3.so': No such file or directory
cp: cannot stat `libborqt-6.9.0-qt2.3.so': No such file or directory
grep: /etc/ld.so.conf: No such file or directory
root@john-desktop:/home/john#


---

### Post by ramjet_1953 on 2007-09-04
If you go here and look carefully,

[http://www.freebyte.com/linux/libraries/](http://www.freebyte.com/linux/libraries/)

You will see that the command is [COLOR="Blue"]./install.sh[/COLOR]

The[COLOR="Blue"] . [/COLOR]is all important

Regards,
Roger :cool:

---

