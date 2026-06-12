---
title: "syslog"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by mudcow007 on 2007-08-28
Hello

im trying to setup syslog but i cant seem to start it :(

i have successfully installed sysklogd (i think)

i have tried running "/etc/init.d/sysklog stop; /etc/init.d/sysklog start"

but it brings up a No such file or directory

im trying to capture logs off a router type device 

any ideas?

thanks

---

### Post by dstew on 2007-08-28
Although the package name is **sysklog**, the utility names are **syslog** and **klog**. Similarly, the daemon names are **syslogd** and **klogd**. So, the command to restart the syslog daemon after you change the **/etc/syslog.conf** file would be:
```
/etc/init.d/syslogd restart
```

---

### Post by grey.rabbit on 2007-08-30
The command that works for me is

```
sudo /etc/init.d/sysklogd restart
```

To check that this is really doing a restart you can do 

```
cat /var/run/syslogd.pid 
```

before and after the first command. It should have changed.

---

