---
title: "TFTP server"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by jimmy85 on 2007-05-15
Somebody kow how can I set a TFTP server in ubuntu?

Thanks for your help.

---

### Post by Cypher on 2007-05-15
You have a couple of options, **atftpd** and **tftpd-hpa**. Install either with APT. Both of them will provide startup scripts in /etc/init.d or you could spawn them (preferred way) through XINETD.

---

### Post by tlsarles on 2007-08-22
I apt-got atftp
Now, does anyone know where the root defaults to, or how to set the root dir?

---

### Post by PacketCollision on 2007-08-22
It looks like atftpd's config is specified in /etc/default/atftpd (or /etc/initd.conf if started from inetd, and it defaults to /tftpboot.  (This info is also in the man pages, although I found it by reading the startup script in /etc/init.d/atftpd).

---

### Post by tkowalski22 on 2007-11-15
Same problem here.  I have searched the net up and down and I can't find a good, step by step guide or how-to for installing a TFTP server either.

No wonder there is so much frustration with Linux (Although I love Ubuntu)

If anyone can find a good install guide for TFTP and/or SYSLOG, linking it would be greatly appreciated....

Thanks

---

### Post by PacketCollision on 2007-11-19
> **tkowalski22 said:**
> Same problem here.  I have searched the net up and down and I can't find a good, step by step guide or how-to for installing a TFTP server either.

No wonder there is so much frustration with Linux (Although I love Ubuntu)

If anyone can find a good install guide for TFTP and/or SYSLOG, linking it would be greatly appreciated....

Thanks
Guide:
1) sudo apt-get install atftpd
2) edit config files mentioned above.
3) sudo /etc/init.d/atftpd start (or some such)

As for syslog, it's installed by default.  What are you trying to do with it?

---

### Post by davidgarcin on 2007-11-21
hey all - 
Try this how-to:

[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

It's very clear, and it seems to work for everyone..... except me.  My situation is a little different though, the client is a Freescale M5275EVB development board....

-Dave

---

