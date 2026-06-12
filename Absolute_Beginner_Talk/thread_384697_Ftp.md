---
title: "Ftp"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by RED WIND on 2007-03-14
I want to setup a ftp server but my ISP blocks port 20 how can I change it so it dont work on 20

---

### Post by irwa82 on 2007-03-14
Hi,

You did not mention which ftp daemon your using. If you are using proftpd you can edit /etc/proftpd.conf and change port 21 to any port you want then restart proftpd with /etc/init.d/proftpd restart.

I imagine that other ftp daemons would allow you to do the same thing in their config.

Kind Regards,
Anthony Irwin

---

### Post by RED WIND on 2007-03-14
yeah I know I change that port but FTP uses 2 ports. Port 20 and 21. 21 is used to send commands on. and 20 is used to transfer the files and provide a list.

---

