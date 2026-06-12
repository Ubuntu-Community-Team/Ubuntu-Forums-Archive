---
title: "Ubuntu as Time Machine server"
date: 2021-10-31
forum: Apple Hardware Users
---

### Post by mapomme1108 on 2021-10-31
Hello,


I want to use a pc running Ubuntu 20.04 as a Time Machine server.


I installed netatalk and populated the /etc/netatalk/afp.conf file as follows:

```
[Global]log level = default:warn
log file = /var/log/afpd.log
hosts allow = 192.168.1.1/24
spotlight = yes


[TimeMachine]
# is this machine a time machine?
time machine = yes
# directory for time machine data on server
path = /home/francois/system_backup/TimeMachine
# the max size of the data folder (in Mb)
vol size limit = 980000
# users with access to time machine
valid users = francois
```

I managed to backup my MacBook but when I want to restore it from recovery mode, connection to the Time Machine server is not possible.
I have an error message telling me to contact my system administrator.


How to configure the server to be able to connect from the recovery mode of the MacBook?


Thanks for your help.

---

