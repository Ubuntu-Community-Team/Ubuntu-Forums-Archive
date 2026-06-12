---
title: "Firewall configuration to allow printing"
date: 2012-06-01
forum: Any Other OS
---

### Post by MonctonJohn on 2012-06-01
Here is a picture I did that represents my LANs (it was quick and dirty): 
[http://i.imgur.com/MqqIA.png]("http://i.imgur.com/MqqIA.png")

I would like all the clients in the 10.25.1.0 network to be able to access the Linux router for SMB and mysql (XBMC)

Also I would like all the 10.25.1.0 clients to be able to access the printer at 11.25.1.24.

Now for the 2nd LAN (11.25.1.0) I would like these clients to only be able to access each other and the internet, but not access anything in the 10.25.1.0 network and printer access is not necessary.

I'm using webmin to try to achieve this but I'm having some issues.

I have a static route set in the internet connected router to forward all requests for 11.25.1.0 to gateway 10.25.1.120.

iptables -L:
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  localhost            anywhere            
ACCEPT     all  --  10.25.1.0/24         anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  10.25.1.0/24         11.25.1.24          
ACCEPT     all  --  11.25.1.24           10.25.1.0/24        

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

iptables -t nat -L:
```
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
```

So far I am able to browse the smb share from the windows host to the linux host/router and I am able to ping the printer but I can't reach the printer otherwise. Can someone help me finish this configuration?

---

### Post by MonctonJohn on 2012-06-01
Finally figured this out. I had to masquerade all requests from the 10.25.1.0 network destined for the printer

iptables -t nat -L:
```
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  10.25.1.0/24         11.25.1.24
```

---

