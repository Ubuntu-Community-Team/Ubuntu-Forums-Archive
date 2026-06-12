---
title: "vpnc -connect /etc/vpnc.conf   not working in Ubuntu. Why ??"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-04-15
vpnc -connect /etc/vpnc.conf   not working in Ubuntu. Why ??
  
Thank you !

pat

---

### Post by cwaldbieser on 2006-04-15
[QUOTE=patrick295767]vpnc -connect /etc/vpnc.conf   not working in Ubuntu. Why ??
  
Thank you !

pat[/QUOTE]
What exactly is not working?  I use vpnc without the -connect option you gave, and it generally works fine.  e.g.
```

$ sudo vpnc ./myconfig.conf

```

---

### Post by patrick295767 on 2006-04-15
I did this : 
If you have 5.10 ubuntu:
1) Install vpnc

if no internet to install it
[http://packages.ubuntu.com/breezy/net/vpnc](http://packages.ubuntu.com/breezy/net/vpnc).
sudo dpkg -i /pad/naar/vpnc-pakket
2) sudo nano /etc/vpnc.conf:
Interface name vpnlink
IPSec gateway IP_address
IPSec ID ipsecclient
IPSec secret the_secret
Xauth username your_username
3) start vpn : sudo vpnc
4) stop vpn: sudo vnpc-disconnect 
  
And then, I did : 
```
vpnc -connect /etc/vpnc/default.conf
```

and it asked the ID secret ... bla bla 
It says : enter IPSec gateway address: ...
...
same result with :
```
vpnc  /etc/vpnc/default.conf
```
    
It's apparently not reading the config file /etc/vpnc/default.conf ...

strange isnt it ,?
(I would like to make it rather more automatic .... I saw that some modprobe could be done ... hmm) 

thank you

---

### Post by cwaldbieser on 2006-04-16
[QUOTE=patrick295767]I did this : 
If you have 5.10 ubuntu:
1) Install vpnc

if no internet to install it
[http://packages.ubuntu.com/breezy/net/vpnc](http://packages.ubuntu.com/breezy/net/vpnc).
sudo dpkg -i /pad/naar/vpnc-pakket
2) sudo nano /etc/vpnc.conf:
Interface name vpnlink
IPSec gateway IP_address
IPSec ID ipsecclient
IPSec secret the_secret
Xauth username your_username
3) start vpn : sudo vpnc
4) stop vpn: sudo vnpc-disconnect 
  
And then, I did : 
```
vpnc -connect /etc/vpnc/default.conf
```

and it asked the ID secret ... bla bla 
It says : enter IPSec gateway address: ...
...
same result with :
```
vpnc  /etc/vpnc/default.conf
```
    
It's apparently not reading the config file /etc/vpnc/default.conf ...

strange isnt it ,?
(I would like to make it rather more automatic .... I saw that some modprobe could be done ... hmm) 

thank you[/QUOTE]

That is odd.  What if you just create a config file in your home directory and try to use that?  Maybe there is a read permission problem?

Otherwise, maybe you could type the info in a file and then do something like:
```

$ sudo vpnc < my_connect_info.txt

```

---

