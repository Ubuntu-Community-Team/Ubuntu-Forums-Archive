---
title: "how to make log files..?"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-10-07
Hi All,

how can i make this save to amule.log ??

logger -f ~/amule.log amule stopped restarting...

it just saves it in messages all the time...

thanks

---

### Post by milosz.galazka on 2007-10-09
If for example syslog falicity local3 is not used then you can use
```
logger -p local3.info  my example
```
then configure syslog daemon by editing configuration file
```
sudo vi /etc/syslog.conf 
```
and adding similar line
```
local3.info                     /path/test.log
```
then just restart it by executing
```
sudo /etc/init.d/sysklogd restart
```
and try it :)

Remember to read manuals :)
```
man -k syslog
```


The easiest way to achieve simple logging is to use
```
echo test >> /path/test.log
```

PS. There could be some mistakes as I am almost sleeping now :)

---

