---
title: "Unable to establish communication between ISPConfig Server em Zabbix Server"
date: 2017-11-15
forum: Any Other OS
---

### Post by shutdown98 on 2017-11-15
Hey guys,

I need some help with my setup... I have 2 instances on Google Cloud Platform, one running ISPConfig (10.154.0.15) and another running as monitoring server with Zabbix (10.154.0.2) installed.
The two instances are in the same subnet and they were supposed to communicate between them.

The problem is that after about 4 minutes of up time on the ISPConfig Server, it stops to communicate with que Zabbix, I can't even ping the two machines.
Even more strange is that if I start pinging the ISPConfig server with Zabbix and then reboot the ISPConfig server it suddenly starts to ping it, then stops (time to reboot the machine) and starts again, and after 4 minutes it stops again.

The gateway for the servers is 10.154.0.1 and I have Internet on the two machines like supposed to. I can ping both machines from outside and I have even created a third instance for testing purposes and everything runs like normal except this two machines that cannot communicate.

Here is what I have tried already:
-Whitelisted the Zabbix Server on fail2ban;
-Disable UFW firewall
-Disable fail2ban itself
-Tried to move the 2 machines to another custom VPC.
-Allowed all ports on the internal network (10.154.0.0/20)

---

### Post by howefield on 2017-11-15
Moved to the "*Any Other OS*" forum

---

