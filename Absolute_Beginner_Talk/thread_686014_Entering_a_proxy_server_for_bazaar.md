---
title: "Entering a proxy server for bazaar"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Georgie.Mathews on 2008-02-02
Hey there

Im trying to install  the curves for awn and it requires bazaar which i have already installed. This is the version I am running :```

gmathews@The1337UbuntuBox:~$ bzr version
Bazaar (bzr) 1.0.0
  Python interpreter: /usr/bin/python 2.5.1.final.0
  Python standard library: /usr/lib/python2.5
  bzrlib: /usr/lib/python2.5/site-packages/bzrlib
  Bazaar configuration: /home/gmathews/.bazaar
  Bazaar log file: /home/gmathews/.bzr.log


```
 Now I am using a university proxy, how do i configure bazaar because i cant find .bazaar in my home directory. I need to set bazaar to use the proxy I am using as I get this error:
```

gmathews@The1337UbuntuBox:~$ bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
bzr: ERROR: Invalid http response for http://bazaar.launchpad.net/%7Eawn-curves-team/awn/awn-curves/.bzr/branch-format: Unable to handle http code 407: Proxy Authentication Required


```

Thanks for your help..Appreciated :):):)

---

### Post by dcstar on 2008-02-03
> **Georgie.Mathews said:**
> Hey there

Im trying to install  the curves for awn and it requires bazaar which i have already installed. This is the version I am running :```

gmathews@The1337UbuntuBox:~$ bzr version
Bazaar (bzr) 1.0.0
  Python interpreter: /usr/bin/python 2.5.1.final.0
  Python standard library: /usr/lib/python2.5
  bzrlib: /usr/lib/python2.5/site-packages/bzrlib
  Bazaar configuration: /home/gmathews/.bazaar
  Bazaar log file: /home/gmathews/.bzr.log


```
 Now I am using a university proxy, how do i configure bazaar because i cant find .bazaar in my home directory. I need to set bazaar to use the proxy I am using as I get this error:
```

gmathews@The1337UbuntuBox:~$ bzr co http://bazaar.launchpad.net/~awn-curves-team/awn/awn-curves awn-curves
bzr: ERROR: Invalid http response for http://bazaar.launchpad.net/%7Eawn-curves-team/awn/awn-curves/.bzr/branch-format: Unable to handle http code 407: Proxy Authentication Required


```

Thanks for your help..Appreciated :):):)

Try System-Preferences-Network Proxy.

---

### Post by calagan on 2008-05-06
Hi,

I'm behind proxy with authentication defined in System-Preferences-Network Proxy, but I'm getting the error below.
```
Unable to handle http code 407: Proxy Authentication Required
```

I also added added the line below in my /etc/bash.bashrc file without any improvement:
```
export http_proxy="http://myuser:mypaswd@myproxy:port"
```

---

### Post by Georgie.Mathews on 2008-07-04
Im sure bazaar does not take the proxy settings from bash.src so it wont work like that. Hence, we need to configure bazaar with its own proxy server.

---

