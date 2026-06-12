---
title: "how to detect internal modem???"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-02-09
i m usin dell inspiron 6000 laptop

but gnomeppp is not detectin the internal modem ?

how to get the modem detected.

---

### Post by nixclusive on 2006-02-09
From ubuntuguide.org:

```
Q: How to identify Modem chipset?
To install Modem chipset identifier 

wget -c http://frankandjacq.com/ubuntuguide/scanModem.gz
gunzip -c scanModem.gz > scanModem
chmod +x scanModem
sudo cp scanModem /usr/bin/

To identify Modem chipset 

sudo scanModem
gedit Modem/ModemData.txt
```

---

### Post by wolfmaniac on 2006-02-10
it returned the following message


rajat@linux:~$ tar xzf automatix-ubuntu_v3.1.tar.gz
tar: automatix-ubuntu_v3.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
rajat@linux:~$ wget -c [http://frankandjacq.com/ubuntuguide/scanModem.gz](http://frankandjacq.com/ubuntuguide/scanModem.gz)
--23:23:10--  [http://frankandjacq.com/ubuntuguide/scanModem.gz](http://frankandjacq.com/ubuntuguide/scanModem.gz)
           => `scanModem.gz'
Resolving frankandjacq.com... 66.246.156.115
Connecting to frankandjacq.com|66.246.156.115|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
23:23:12 ERROR 404: Not Found.

---

### Post by cogadh on 2006-02-10
The Inspiron 6000 has a Winmodem, which will not be detected without some additional software. See [http://www.math.ucla.edu/~jimc/insp6000/p-net.html](http://www.math.ucla.edu/~jimc/insp6000/p-net.html) for a good starting point.

---

