---
title: "Running openldap at system boot"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Kasyx on 2008-03-14
Hi,

I am wondering how to go about setting a process (openldap) to run when the system boots. I have checked and slapd is in /etc/init.d, yet it does not start automatically at boot. How could I fix this?

Thanks

---

### Post by SpaceTeddy on 2008-03-14
create a softlink in the appropriate runlevel - i.e. if you want ldap to start when entering runlevel 2 (normal runlevel for ubuntu), then place a link in /etc/rc2.d to the start/stop script  in /etc/init.d

you should also follow the convetions of the softlink nameing.

this is a sample how it could work
> cd /etc/rc2.d
sudo ln -s ../init.d/slapd S20slapd

---

