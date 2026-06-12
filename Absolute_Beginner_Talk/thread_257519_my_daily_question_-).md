---
title: "my daily question :-)"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Imsati on 2006-09-14
Trying to install w32codecs with Kubuntu (via the Terminal) and get this message

jason@jasonK:~$ wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.de](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.de)
--16:55:58--  [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.de](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.de)
           => `w32codecs_20060611-1plf1_i386.de'
Resolving packages.freecontrib.org... 88.191.21.245
Connecting to packages.freecontrib.org|88.191.21.245|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:55:58 ERROR 404: Not Found.


It went fine previously with both Ubuntu and Kubuntu. Just a glitch? Try again later maybe?

---

### Post by haxer on 2006-09-14
Maybe the server is down or new adress maybe  :S

---

### Post by Imsati on 2006-09-14
Never mind.

Heh...Stupid 'B'...

I'm an idiot. Feel free to poke fun at :-)

~Jay

---

### Post by Metacarpal on 2006-09-14
If you have the PLF repositories added to your system already, you can also install the package with:
```
sudo aptitude install w32codecs
```

---

