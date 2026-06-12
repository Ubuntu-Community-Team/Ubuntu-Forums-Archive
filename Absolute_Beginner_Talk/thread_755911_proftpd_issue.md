---
title: "proftpd issue"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by soeten on 2008-04-15
I have previously set up a proftpd server where the system users automatically can log in via ftp and remain locked in their home directory.

When I use "_adduser $user_" this works perfectly, however If I use "_useradd -g 1121 -s /bin/false -m -d /home/$user -p $pass $user_" they cant connect to the ftp. Ive tried to disable the option "require valid shell to login" in the proftpd.conf, but it still doesn't work.

Any ideas ? : |

---

### Post by superprash2003 on 2008-04-15
consider using gproftpd - its a gui for proftpd and can be installed via synaptic.. it would make it more easier to configure the ftp server

---

