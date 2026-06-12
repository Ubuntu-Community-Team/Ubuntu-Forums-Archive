---
title: "how to execute a process at the beginning"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by herbert tamayo on 2008-01-23
hi, I want that apache2 starts automatically everytime I init linux, in this moment I have to do apache2 start, my question is where I have to configure this line to start apache2 automatically?

thanks

---

### Post by eggdeng on 2008-01-23
Paste the command (with a trailing ampersand) into /etc/init.d/rc.local just after the #!/bin/sh, as follows:
```
#!/bin/sh 
/usr/sbin/apache2 -k start &
```
Alternatively, download the boot up manager 
```
sudo apt-get install bum
```
to have a nice graphical interface for this sort of task.

---

### Post by macogw on 2008-01-23
You don't need the boot up manager to set that.  System > Admin > Services lets you set if Apache2 starts at boot or not, and that's part of a default Ubuntu install.

---

