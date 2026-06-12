---
title: "[SOLVED] Postfix Question"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by techno-wiz on 2008-03-11
I have postfix installed on a Ubuntu server to send nagios alerts to our main mail server. It is working BUT the emails received are only from nagios-svr instead of nagios-svr.domain.com.


Can someone tell me where the source address is configured to I can change it to the FQDN instead of just the host?

---

### Post by glennric on 2008-03-11
You will probably need to edit the file /etc/hosts and change nagios-svr to nagios-svr.domain.com

---

### Post by techno-wiz on 2008-03-11
Thanks for the help. Tried editing the hosts file and rebooting but still the same. Went back and looked more at my /etc/postfix/main.cf file and saw it referencing a file called mailname. Looked at /etc/mailname and it only had my hostname. Edited it and restarted postfix. Working like a charm now!

---

