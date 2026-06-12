---
title: "Interent connection sharing with Ubuntu."
date: 2005-07-15
forum: Absolute Beginner Talk
---

### Post by silent-red on 2005-07-15
Hi,

Could anyone please help point out a link regarding my thread? Before I have posted I did used the search tool of this site, unforunately, I did not find what I was looking for.

Hardware list:
3 PCS (2 XP, 1 Ubuntu)
1 Switch CNET
1 USB Speedtouch modem

I'm planning on using the Ubuntu box to share my internet connection. IP address (ubuntu) is 192.168.0.1 and for xp it is 192.168.0.2. I say there is no connection between the two, because I can't even ping the xp box,  

Here is the actual message
```

PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.0.2 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5020ms


```

---

### Post by jasmuz on 2005-07-15
Maybe this is a step in the right direction:

[http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)

---

### Post by SKLP on 2005-07-15
If this can be of any help, try it:
```
#!/bin/bash

### made by sklp, I am not responsible for problems, errors, typos, bugs and/or security flaws :) GLHF!

## This script needs to be started at boot. When you made changes simply run the script manually.
## eth0 is the LAN-connected interface
## eth1 is the Internet-connected interface

# Enable IP Forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

# Clean up iptables (flush it)
iptables -F
iptables -t nat -F
iptables -X

# Enable IP MASQUERADING/NAT
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

# Set firewall policies (default behaviour)
iptables -P INPUT DROP
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

# Allow all connections not from eth1
iptables -A INPUT -i ! eth1 -j ACCEPT

# Allow all ICMP connections (like ping)
iptables -A INPUT -p ICMP -j ACCEPT

# Allow all already established connections
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


## Make holes in the firewall for running different services

# Open HTTP (for running a web server)
iptables -A INPUT -p tcp --dport 80 -j ACCEPT

# Open FTP (for an internet-accessible FTP server) NOT RECOMMENDED FOR SECURITY -- USE SSH/SFTP INSTEAD IF POSSIBLE
#iptables -A INPUT -p tcp --dport 21 -j ACCEPT

# Open SSH (for OpenSSH server: remote login and SFTP)
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

# Open SMTP (for running a local mail server)
iptables -A INPUT -p tcp --dport 25 -j ACCEPT

# Some other port (Example)
#iptables -A INPUT -p udp --dport 4455 -j ACCEPT


# ------------- Port Forwarding -------------
## NOTE: If you port forward a port you don't need to "open" it like above

# <+++++ nameofcomputer2 (192.168.0.2) +++++>

#Example 1 (forwards port 3000 tcp only to "nameofcomputer2")
iptables -A PREROUTING -t nat -p tcp -i eth1 --dport 3000 -j DNAT --to 192.168.0.2

# <----- ----->



# <+++++ nameofcomputer3 (192.168.0.3) +++++>

#Example 2 (forwards ports 4000-5000 all protocols to "nameofcomputer3")
iptables -A PREROUTING -t nat -p all -i eth1 --dport 4000:5000 -j DNAT --to 192.168.0.3

# <----- ----->
```

---

