---
title: "wine_problem"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by jamil_1 on 2007-03-19
i have tried to run wine but it gives the following error

[root@localhost root]# wine
wine: creating configuration directory '/root/.wine'...
/usr/bin/wineserver: relocation error: /usr/bin/wineserver: symbol epoll_create, version GLIBC_2.3.2 not defined in file libc.so.6 with link time reference
wine: wineprefixcreate failed while creating '/root/.wine'.
[root@localhost root]#

i have tried wine  as simple unpriviliged user instead of root but got the same error


i have red hat 9. i obtained the rpm file from winehq.com. file name is   
                       wine-0.9.2-1fc1winehq.i686.rpm                   
Don't ask me to upgrade

---

### Post by justleen on 2007-03-19
How bout upgrading to Ubuntu? Or finding a Red Hat Forum?  :)

As to answering your question:
From the WineHQ forums
> 
You need to compile from source, or apply all the security updates.


---

### Post by jamil_1 on 2007-03-19
well i have put the same question on LQ.com but they are slow in response

---

### Post by justleen on 2007-03-19
been thinking on this a bit.. I think i had the same when trying to install wine, and applying the security pathches did the trick for me. 

in very very short: (see winehq for patch details)
- download the source, unpack
- download the patches, unpack
- apply the patches
- compile wine

---

### Post by eljalill on 2007-03-19
...that would be another reason for running ubuntu.. :) ?
To your question: Just wandering whether you have linux-libc-dev installed?
And build essentials of course also?

---

### Post by zvacet on 2007-03-19
Download wine from synaptic.You downloaded rpm file and want to install it in Ubuntu.That is not working.If you still have your rpfm file do this
```
sudo alien file_name rpm
```
That will convert rpm to deb,but you have alien installed. It´s in synaptic.

---

