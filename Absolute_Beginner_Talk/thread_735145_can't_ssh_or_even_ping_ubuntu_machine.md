---
title: "can't ssh or even ping ubuntu machine"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Exgbear on 2008-03-25
Hello,

I've been completely unable to ping or ssh to my ubuntu machine.

I have no fire wall and no iptables.
output of iptables -nL

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

Output of netstat -tnl

~# netstat -tnl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     



sshd_config

# What ports, IPs and protocols we listen for
Port 22

# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::

ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

Output of ifconfig

bnoel@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:85:B1:21:94  
          inet addr:192.168.1.251  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::211:85ff:feb1:2194/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1859 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2182115 (2.0 MB)  TX bytes:261066 (254.9 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4488 (4.3 KB)  TX bytes:4488 (4.3 KB)

The machines are on the same subnet and gateway and all that.

Here's a copy of /etc/network/interfaces
auto eth0
iface eth0 inet static
address 192.168.1.251
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.3.255
network 192.168.1.0


The ip address has also been added to my /etc/hosts on my Vista machine that I have successfully run ssh to other devices with before.

This is a pretty big problem, so any help would be greatly appreciated.

---

### Post by OffAxis on 2008-03-25
can you ping the Vista machine from the ubuntu machine?

Is there a reason you're broadcasting 192.168.3.255 instead of 192.168.1.255?

Can you see both machines from the router setup page?

---

### Post by prshah on 2008-03-25
> **Exgbear said:**
> 
eth0      Link encap:Ethernet  HWaddr 00:11:85:B1:21:94  
          inet addr:192.168.[color=blue]1.251[/color]  Bcast:192.168.[color=blue]3.255[/color]  Mask:255.255.255.0
          inet6 addr: fe80::211:85ff:feb1:2194/64 Scope:Link

address 192.168.[color=red]1.251[/color]
netmask 255.255.255.0
broadcast 192.168.[color=red]3.255[/color]

This is a pretty big problem, so any help would be greatly appreciated.

1) disable ipv6 if you are not using it (and you don't seem to be)
2) Why is your broadcast IP different from your machine's IP net? ie, machine is on "...1.251" and broadcast is "...3.255" Either correct your broadcast address or your subnet mask.

---

### Post by Exgbear on 2008-03-25
I fixed my broadcast address and restarted.  Still the same results.  Actually, no I can't see my vista machine from the ubuntu machine.

Also, I don't know how to disable ipv6.

I don't have access to the router page.

---

### Post by Exgbear on 2008-03-25
Well I'm all set.  It turns out that we were connected to the wrong router.  Simple cable switch and everything is good now.

---

