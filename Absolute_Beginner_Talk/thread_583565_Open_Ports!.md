---
title: "Open Ports!"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Trzone on 2007-10-20
Hi as you can see attached i have some odd ports open after i upgraded from 7.04  before the upgrade, none of these ever appeared to be open.

---

### Post by dynamethod on 2007-10-20
try this site: [http://www.linux-sec.net/Audit/nmap.test.gwif.html](http://www.linux-sec.net/Audit/nmap.test.gwif.html)

and see what the results are

---

### Post by Woei on 2007-10-20
> **Trzone said:**
> Hi as you can see attached i have some odd ports open after i upgraded from 7.04  before the upgrade, none of these ever appeared to be open.

To find out what programs are behind these listening sockets, do something like

```
sudo netstat --listen -p
```

The -p option will reveal the process PID and name. You're only seeing the responsible process if you're the owner, or root.

For example, on my 7.10 machine, this prints:

```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 *:43791                 *:*                     LISTEN     4444/rpc.statd      
tcp        0      0 *:sunrpc                *:*                     LISTEN     4426/portmap        
tcp        0      0 localhost:ipp           *:*                     LISTEN     5109/cupsd          
tcp        0      0 *:50428                 *:*                     LISTEN     -

```

Which is the RPC portmapper, the remote file locking daemon (for NFS) and the cups print server.

---

### Post by aktiwers on 2007-10-20
What is the name of that app on your screenshot?

---

### Post by Pumalite on 2007-10-20
php-net-portscan, I think.

---

### Post by Trzone on 2007-10-20
From Linux- Sec.net


....   
..Starting nmap 3.93 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2007-10-20 11:57 PDT..   
..Warning:  OS detection will be MUCH less reliable because we did not find at least 1 open and 1 closed TCP port..   
..Interesting ports on  cpe-66-67-1-1.rochester.res.rr.com (66.67.1.1): ..   
..(The 1226 ports scanned but not shown below are in state: filtered)..   
..PORT    STATE  SERVICE..   
..113/tcp closed auth.. auth should be turned on for your Mail Server  
..Device type: load balancer|firewall|broadband router|general purpose..   
..Running: Cisco embedded, Cisco PIX 5.X|6.X, D-Link embedded, Microsoft Windows NT/2K/XP..   
..OS details: Cisco CSS 11501 Content Services Switch, Cisco Localdirector load balancer, Cisco PIX Firewall (PixOS 5.2 - 6.1), Cisco Firewall (PIX 6.1.4 - 6.2.2), Cisco PIX Firewall running PIX 6.2 - 6.3.3, DI-701 Residential Gateway or KA9Q NOS  
 


attached is the netstat --listen -p

---

### Post by Woei on 2007-10-20
> **Trzone said:**
> From Linux- Sec.net


....   
..Starting nmap 3.93 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2007-10-20 11:57 PDT..   
..Warning:  OS detection will be MUCH less reliable because we did not find at least 1 open and 1 closed TCP port..   
..Interesting ports on  cpe-66-67-1-1.rochester.res.rr.com (66.67.1.1): ..   
..(The 1226 ports scanned but not shown below are in state: filtered)..   
..PORT    STATE  SERVICE..   
..113/tcp closed auth.. auth should be turned on for your Mail Server  
..Device type: load balancer|firewall|broadband router|general purpose..   
..Running: Cisco embedded, Cisco PIX 5.X|6.X, D-Link embedded, Microsoft Windows NT/2K/XP..   
..OS details: Cisco CSS 11501 Content Services Switch, Cisco Localdirector load balancer, Cisco PIX Firewall (PixOS 5.2 - 6.1), Cisco Firewall (PIX 6.1.4 - 6.2.2), Cisco PIX Firewall running PIX 6.2 - 6.3.3, DI-701 Residential Gateway or KA9Q NOS  


Shut tight

> attached is the netstat --listen -p
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 localhost:ipp           *:*                     LISTEN     4942/cupsd          
udp        0      0 *:32769                 *:*                                5538/avahi-daemon:  
udp        0      0 *:bootpc                *:*                                5754/dhclient       
udp        0      0 *:mdns                  *:*                                5538/avahi-daemon:  


Only a print server, a dhcp client and an [Avahi daemon]("http://avahi.org/wiki/AboutAvahi"). All part of a standard Ubuntu desktop installation, nothing to worry about. Besides, you're behind a NAT device, which means that unless you explicitly forward ports from said router/NAT device to a machine running malicious or vulnerable software (which it does not, as the scan indicates), you are not vulnerable to remote initiated attacks.

---

### Post by n3tfury on 2007-10-20
> **aktiwers said:**
> What is the name of that app on your screenshot?

System>Administration>Network Tools

---

### Post by Trzone on 2007-10-20
Thank you! I was only concerned about security risks :popcorn:

---

