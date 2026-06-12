---
title: "APT problems"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by hvc123 on 2008-03-14
Hi all,

i have a problem with apt-get . i am using Gutsy and im behind a firewall (squid port 80)

i have set up the apt.conf and added the proxy address 
i.e.
Acquire::http::Proxy "PROXYADDRESS:80";
obviously i have removed my proxy address.

now all was good until i stated to play with conky and scripts.

i have to use the export http_proxy="PROXYADDRESS:80" to get some of the scripts to work.
this in turn has knackered my apt-get access. however not is all lost as synaptic still works fine.
below is the output from apt-get
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/source/Sources.gz)  Cannot initiate the connection to 80:80 (0.0.0.80). - connect (22 Invalid argument)
Reading package lists... Done


any ideas ?  thanks

---

### Post by hvc123 on 2008-03-14
no one ?

---

