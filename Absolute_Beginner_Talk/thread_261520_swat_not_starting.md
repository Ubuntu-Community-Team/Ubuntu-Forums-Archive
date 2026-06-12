---
title: "swat not starting"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by crokett on 2006-09-20
trying to get swat running to administer Samba.

According to the docs I have the proper entry in /etc/inetd.conf to start it but a netstat does not show SWAT as running - open ports start somewhere north of 14000. I tried kill -HUP inetd as per readmes to restart inetd daemon but that failed with kill saying what sounded like inetd is not a running process. Also tried a reboot. 

Found some info to check /etc/rc.tcpip - I will do this tonight.

Any other things to check?

I am not finding an xinetd config file in /etc so assume Ubuntu does not use this?

---

