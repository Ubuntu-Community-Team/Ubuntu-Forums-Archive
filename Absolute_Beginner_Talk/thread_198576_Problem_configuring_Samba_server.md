---
title: "Problem configuring Samba server"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by dross on 2006-06-17
Hello,

I am trying to setup a Samba print/file server using this tutorial: [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

and have run into a bizarre problem...after I finished configuring Samba (page 4 of the tutorial), I tried: ```
smbclient -L localhost -U%
``` and got back "error connecting to 127.0.0.1:445 (no route to host)".  So I tried to ping localhost and couldn;t get a connection, but I could successfully ping the static IP address that I setup for the server...so I'm just stumped about what's going on. If anyone has any thoughts it would be much appreciated.  Thanks!

---

### Post by gerbman on 2006-06-17
[QUOTE=dross]Hello,

I am trying to setup a Samba print/file server using this tutorial: [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

and have run into a bizarre problem...after I finished configuring Samba (page 4 of the tutorial), I tried: ```
smbclient -L localhost -U%
``` and got back "error connecting to 127.0.0.1:445 (no route to host)".  So I tried to ping localhost and couldn;t get a connection, but I could successfully ping the static IP address that I setup for the server...so I'm just stumped about what's going on. If anyone has any thoughts it would be much appreciated.  Thanks![/QUOTE]Make sure the loopback interface is configured. Check the output of "ifconfig" and look at the entry for "lo" (its IP address should be 127.0.0.1). If that's not the case, do the following:```
sudo ifdown lo
sudo ifup lo
```and check "ifconfig" again.

---

### Post by dross on 2006-06-17
That did it.  Thanks a lot, gerbman!

---

### Post by gerbman on 2006-06-17
[QUOTE=dross]That did it.  Thanks a lot, gerbman![/QUOTE]You're welcome :)

---

