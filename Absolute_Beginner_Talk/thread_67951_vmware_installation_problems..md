---
title: "vmware installation problems."
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by xequence on 2005-09-21
Awhile back I tried to compile vmware. It didnt work... So I got a RPM and alien-ed it to a deb. I installed it fine, but when I try to run it, it doesent come up. I run it from the terminal, it gives me an error. Here is my terminal stuff, from the install to now.

> patrick@ubuntu:~$ sudo dpkg -i /home/patrick/Desktop/vmwareworkstation_5.0.0-13125_i386.deb
Password:
Sorry, try again.
Password:
Selecting previously deselected package vmwareworkstation.
(Reading database ... 65011 files and directories currently installed.)
Unpacking vmwareworkstation (from .../vmwareworkstation_5.0.0-13125_i386.deb) ...
Setting up vmwareworkstation (5.0.0-13125) ...

patrick@ubuntu:~$ vmware
/usr/bin/vmware: line 85: /etc/vmware/locations: No such file or directory
/usr/bin/vmware: line 183: /lib/wrapper-gtk24.sh: No such file or directory
/usr/bin/vmware: line 183: exec: /lib/wrapper-gtk24.sh: cannot execute: No such file or directory
patrick@ubuntu:~$ sudo vmware
/usr/bin/vmware: line 85: /etc/vmware/locations: No such file or directory
/usr/bin/vmware: line 183: /lib/wrapper-gtk24.sh: No such file or directory
/usr/bin/vmware: line 183: exec: /lib/wrapper-gtk24.sh: cannot execute: No such file or directory
patrick@ubuntu:~$


---

### Post by weblordpepe on 2007-11-23
> **xequence said:**
> Awhile back I tried to compile vmware. It didnt work... So I got a RPM and alien-ed it to a deb. I installed it fine, but when I try to run it, it doesent come up. I run it from the terminal, it gives me an error. Here is my terminal stuff, from the install to now.I'm stuck there too. Where did you get the sauce code from?

---

