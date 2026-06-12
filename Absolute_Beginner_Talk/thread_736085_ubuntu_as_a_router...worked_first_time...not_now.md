---
title: "ubuntu as a router...worked first time...not now?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-03-26
ok i set up my desktop to server as a router for my notebook. I did this 2 or so weeks ago and it worked fine. after some stupid mistakes i had to reinstall ubuntu and now i cant get my port forwarding to work.

i followed the guide here at: [http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874) this is a great guide and it worked the first time as you can see in my orignal thread here: [http://ubuntuforums.org/showthread.php?t=722368&page=2](http://ubuntuforums.org/showthread.php?t=722368&page=2) .

The first time i had to add

```
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward 
```
to my /etc/rc.local because the system was ingoring the comment put in the /etc/sysctl.conf file.

now when i do

```
cat /proc/sys/net/ipv4/ip_forward
```
it returns a 0 that means port forwarding is not turned on.

any help would be great, it appears to me that now the computer is ignoring both files. even when i load it manually and i get the "1" as a response stating that port forwarding is turned on it still wont work. I have double and triple checked every thing.

thanks for everyones time! :)

---

### Post by SpaceTeddy on 2008-03-26
mhm.. can you post the output of the debugging commands again ? you already said you checked them, but maybe four eyes see more than two :)

```
sudo iptables -L -vnx
sudo iptables -L -vnx --table nat
ifconfig
route -n
sudo netstat -lnp --protocol=inet
```

also, are can the two computers ping each other, and how is the "client" being configured ? static, dhcp ?

---

### Post by waspbr on 2008-03-26
cool, I am tempted to do that but the bad thing would be that I would have to leave my desktop on at all times or I would have to turn it on if i wanted to use my laptop, so I went with the "cheap" way out and got myself a d-link router. Also I dual boot with windouze XP because of work and some gaming...

---

### Post by rockinlinux on 2008-03-26
home@home-desktop:~$ sudo iptables -L -vnx
[sudo] password for home:
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
home@home-desktop:~$ 
__________________________________________________________________________
home@home-desktop:~$ sudo iptables -L -vnx --table nat
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
______________________________________________________________________________
eth1      Link encap:Ethernet  HWaddr 00:02:2A:E1:7E:06  
          inet addr:10.8.16.1  Bcast:10.8.16.0  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xec00 
____________________________________________________________________________
home@home-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
91.192.159.64   0.0.0.0         255.255.255.192 U     0      0        0 eth0
10.8.16.0       0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         91.192.159.65   0.0.0.0         UG    100    0        0 eth0
___________________________________________________________________________
home@home-desktop:~$ sudo netstat -lnp --protocol=inet
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     5495/mysqld         
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     6149/apache2        
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN     5732/hddtemp        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5419/cupsd          
udp        0      0 0.0.0.0:32771           0.0.0.0:*                          5935/avahi-daemon:  
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          5935/avahi-daemon:  
__________________________________________________________________________
I have the notebook set up with the same exact staic IP as before. the desktop has all the same exact info as before as well. i will try to ping and get back to you asap...have to boot the book :)

FYI 

eth0 : internet connection

eth1 : network (connected to the notebook)

---

### Post by rockinlinux on 2008-03-26
just as last time. the notebook with mandriva can ping the desktop but the besktop cannot ping the notebook.

---

### Post by rockinlinux on 2008-03-26
> **waspbr said:**
> cool, I am tempted to do that but the bad thing would be that I would have to leave my desktop on at all times or I would have to turn it on if i wanted to use my laptop, so I went with the "cheap" way out and got myself a d-link router. Also I dual boot with windouze XP because of work and some gaming...

Yeah, my desktop is pretty much on all the time anyways lol the notebook is only used for the wife and when i travel :) stiil need to use the internet to use pat-get and updates for mandriva on the book. I would buy a router but im moving back to the states in a couple months and wont be able to take a router.

---

### Post by rockinlinux on 2008-03-26
btw 


@SpaceTeddy thanks so much as always!! :)

---

### Post by SpaceTeddy on 2008-03-27
the fact that you do not have a dns or dhcp server runnning does not really matter, since basic internet conectivity should be given due to the fact that you can ping. the rest looks rather fine :)

one essential part seems to be missing... 
from your nat table in iptables, (command: iptables -L--table nat -vnx) )there is no masquerade rule which would rewrite your pakets... 

i.e. it should looks like this

> Chain PREROUTING (policy ACCEPT 3991 packets, 414994 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 1291 packets, 62900 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
**    0                0 MASQUERADE  0    --  *      eth0    0.0.0.0/0            0.0.0.0/0           **

Chain OUTPUT (policy ACCEPT 418 packets, 44530 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

without that, your desktop will not hide the laptop and thus the pakets will go into the internet, but cannot find their back to you... can you please post the content of your /etc/rc.local to make sure the commands are run correctly ?

hopefully, that is the problem :)

---

### Post by rockinlinux on 2008-03-27
here it is, im pretty sure its correct:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

/bin/echo 1 > /proc/sys/net/ipv4/ip_forward
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE

```

---

### Post by SpaceTeddy on 2008-03-27
> **rockinlinux said:**
> here it is, im pretty sure its correct:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

**exit 0**

/bin/echo 1 > /proc/sys/net/ipv4/ip_forward
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE

```

yes, it is... just that is stops running at the "exit 0" - copy that to the bottom (below the three commands) and they will run - and thus your internet sharing should work. this way, these commands get ignored :)

---

### Post by rockinlinux on 2008-03-27
lol ok thanks, i didnt even think about that...im going to try it and get back to you in a few

---

### Post by rockinlinux on 2008-03-27
ok that worked great....thanks again! :)

---

