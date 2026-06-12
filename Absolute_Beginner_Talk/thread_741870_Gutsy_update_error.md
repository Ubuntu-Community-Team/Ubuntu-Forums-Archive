---
title: "Gutsy update error"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by bwallum on 2008-04-01
Can anybody help me solve this one please? I cant update Gutsy

This command:-  sudo apt-get install -f

gave me the following error. 

E: Syntax error /etc/apt/apt.conf:3: Extra junk at end of file

How do I correct the error please?

Regards
Bob

---

### Post by kellemes on 2008-04-01
Please post the output of..
```
cat /etc/apt/apt.conf
```

---

### Post by bwallum on 2008-04-01
aquire::http::Proxy"http://proxy.lauder.ac.uk:8080"

---

### Post by kellemes on 2008-04-01
> **bwallum said:**
> aquire::http::Proxy"http://proxy.lauder.ac.uk:8080"

You should have a semicolon at the end of this line..

```
gksudo gedit /etc/apt/apt.conf
```
and append semicolon to line.

---

### Post by bwallum on 2008-04-01
It seems to be a proxy error

This is the proxy line that works for Firefox:- [http://proxy.lauder.ac.uk/](http://proxy.lauder.ac.uk/)

This is (now, thanks to you - solved the error!) the apt.conf file

aquire::http::Proxy"http://proxy.lauder.ac.uk:8080";

Have I got this right now? The update manager now fires up ok but gives the following:

[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2:) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (111 Connection refused)
...
 Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (111 Connection refused)

Thanks for the quick response

---

