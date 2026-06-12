---
title: "Losing my DNS server"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by fredtal on 2006-03-14
It happens a lot where all of sudden I can't find web sites or send email etc.  I check my DNS server and the one provided by my ISP is gone and the default 127.0.0.1 is back.  I haven't a clue as to why it won't stay put.

Fred

---

### Post by alamba on 2006-03-15
Have u tried putting it in systems>>admin>>networking? Are you pulling your IP and DNS info via DHCP?

A

---

### Post by fredtal on 2006-03-15
Yes to both I set my DNS server via networking and my IP is DHCP.  Once I set it it works fine for a while, and then it goes away.

---

### Post by lreyes6 on 2006-03-15
try to put them in the interfaces file 
```
 sudo gedit /etc/network/interfaces 
```
lets asume that you only have one NIC and its named eth0, check for this line 
```

dns-nameservers 

```
if you don't have this line you add it at the end but before auto eth0

and then you put there your dns servers ips separated by spaces

```

dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx

```
save and close the interfaces file after modification and then restart the NIC

```
sudo /etc/init.d/networking restart
```

and that's all that should work any questions post them here

saludos

---

### Post by fredtal on 2006-03-15
That seems to work, I did not have the dns-nameservers line in the file.  One more question, if I use the menus to set the dns server, does it not edit this file?  It seems a bit strange that the two ways of doing something work in different ways.

---

