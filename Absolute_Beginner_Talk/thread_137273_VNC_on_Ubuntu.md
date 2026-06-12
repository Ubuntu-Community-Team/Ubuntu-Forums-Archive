---
title: "VNC on Ubuntu"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by Tixer on 2006-02-27
How do I install VNC on Ubuntu, host an fserve on IRC, and how can I set something so that those programs automatically boot?

---

### Post by gibson on 2006-02-27
> sudo apt-get install vnc


server or client?

---

### Post by patrick295767 on 2006-02-27
```
apt-get install vpnc 
```
or: [http://www.unix-ag.uni-kl.de/~massar/vpnc/](http://www.unix-ag.uni-kl.de/~massar/vpnc/)
  
If you have 5.04 ubuntu:
1) Install vpnc
2) gedit /etc/vpnc.conf :
	Interface name vpnlink
	IPSec gateway IP_address
	IPSec ID ipsecclient
	IPSec secret secret_code
	Xauth username yourusernam
3) start vpn : sudo vpnc-connect
4) stop vpn : sudo vpnc-disconnect
  
  
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

Greetings,

Patrick

---

