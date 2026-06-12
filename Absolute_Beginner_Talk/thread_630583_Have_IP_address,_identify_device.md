---
title: "Have IP address, identify device"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-12-03
I want to identify a device and only have an IP address.
Is there a command I can use to identify if the device is a Computer, Router, Printer, etc?

Carl

---

### Post by jken146 on 2007-12-03
You can do TraceRoute in System > Administration > Network Tools.

---

### Post by wormser on 2007-12-03
There are a couple of tools you can use.  Try nmap and nessus.  Both are in the repositories.  The following nmap command will try to guess the remote OS.

```
sudo nmap -O 192.168.1.1
```

Of course put in whatever IP address of domain name you want.  There are a ton of commands so check the man page.

---

