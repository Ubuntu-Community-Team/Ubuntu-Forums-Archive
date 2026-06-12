---
title: "[SOLVED] FTP server problem"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by spydon on 2008-03-28
Hi

I have setup a vsftpd server on my machine and it worked perfectly fine until we switched router. I have forwarded port 20 and 21 to the machine where I run vsftpd and I can access the ftp from ouside the network by: ```
ftp spydon.is-a-geek.net
``` in a terminal, but I can't connect to it from a browser....

---

### Post by DBrocks on 2008-03-28
What happens when you try to access from a web browser?

---

### Post by DBrocks on 2008-03-28
Try this:

edit the /etc/sysconfig/iptables-config file

Edit the line:

```
 IPTABLES_MODULES=""
```

to read:

```
 IPTABLES_MODULES="ip_nat_ftp"
```

restart iptables. 

Tell me what happens

Good luck!

~Dan

---

### Post by spydon on 2008-04-06
Thx, but that wasnt the problem... I had to add it to something called virtual servers in my router (D-link DIR-635).

---

