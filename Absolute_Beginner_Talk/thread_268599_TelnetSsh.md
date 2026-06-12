---
title: "Telnet/Ssh"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by meseleto on 2006-09-30
I tried installing ssh with this:

sudo apt-get install ssh-server

and this is what i got from the terminal:

Reading package lists... Done
Building dependency tree... Done
Package ssh-server is a virtual package provided by:
  openssh-server 1:4.2p1-7ubuntu3
  ssh-krb5 3.8.1p1-10
  lsh-server 2.0.1cdbs-4
You should explicitly select one to install.
E: Package ssh-server has no installation candidate


How do I explicitly select one to install?

---

### Post by ewl1217 on 2006-09-30
You probably want the openssh-server package. Use the following command to install it:
```
sudo apt-get install openssh-server
```

---

