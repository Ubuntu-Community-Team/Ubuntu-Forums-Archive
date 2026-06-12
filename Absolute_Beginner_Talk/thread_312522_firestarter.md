---
title: "firestarter"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by pavel_kbc on 2006-12-04
hey guys.
how do i add firestarter to gnone startup?

---

### Post by igknighted on 2006-12-04
Someone can correct my if I am wrong here, but I believe iptables starts all the time, and you only need to load the GUI (firestarter) when you are making changes... I could be wrong here tho.  Assuming you are using GNOME, in system->administration->sessions is where you would add a program.  Just enter the command you would put into the terminal to start it ('firestarter' i believe?)

---

### Post by kakalaky on 2006-12-04
You are correct, iptables is run on startup and firestarter is only needed to make changes.

---

### Post by Snowmayne on 2006-12-04
Dang! and here I thought I actually needed to have it up and running all the time :o ](*,) Guess I'll be disabling it from the startup list tonight ;)

---

### Post by pavel_kbc on 2006-12-04
dont you guys know firestarter run as root only ? huh? so its wont work on system->administration->sessions. i knew about it before and i tried it. then i asked for help

---

### Post by yy1124 on 2006-12-06
Another noob question...

What is the need of the Start and Stop firewall button in Firestarter GUI for if the firestater is needed only when updating iptables?

---

### Post by rabid emu on 2006-12-06
I also run firestarter at startup.  It shows how much bandwidth I've been using since startup, which is useful due to university bandwidth limits ](*,) 

To start it up, the only way I know of is to add "gksudo firestarter" to the "sessions" startup programs.  It'll prompt you graphically for your root password when it starts, so if you are restarting gnome/your computer a lot it might get annoying. I suppose you could change permissions to firestarter itself to get around this, but that's a slight security breach.

---

### Post by Wim Sturkenboom on 2006-12-06
The firewall does't necessarily start at boot (it doesn't on my system). If I run *iptables -L -n* after boot, it's empty. The firewall only starts when I start my pppoe.

Further *firestarter* is an easy way to start and stop your iptables, else you have to write your own iptables script(s) to start/stop the firewall when you don't need it. So that's the reason for those buttons.

---

### Post by Peti29 on 2006-12-06
And I thought I was online without a firewall... It's good to know there is one in the background already ;)

---

### Post by yy1124 on 2006-12-06
> **Wim Sturkenboom said:**
> The firewall does't necessarily start at boot (it doesn't on my system). If I run *iptables -L -n* after boot, it's empty. The firewall only starts when I start my pppoe.

Further *firestarter* is an easy way to start and stop your iptables, else you have to write your own iptables script(s) to start/stop the firewall when you don't need it. So that's the reason for those buttons.

Thanks for the explanation.

Thats mean I am running without iptable all the time ><"

I am having problem accessing internet when firestarter is active. The page seems to load forever, I have to turn off firestarter to browse the web again.

I've already enable all the rules to allow all the services to run, did I miss some other setting that make me not able to browse?

---

### Post by pavel_kbc on 2006-12-06
oh man i am happy with no firestarter gui graphical interface. :P

---

### Post by pavel_kbc on 2006-12-06
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

man you have to add firestart on this visudo. not in sessions. i saw this on a menual long time ago :D

---

### Post by Wim Sturkenboom on 2006-12-06
For those interested the output of *iptables -L -n* on my system after starting the pppoe interface:
```
[FONT="Fixedsys"]Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
LSI        all  --  0.0.0.0/0            0.0.0.0/0           

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  196.30.31.193        0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  196.30.31.193        0.0.0.0/0           
ACCEPT     tcp  --  196.46.70.1          0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  196.46.70.1          0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
LSI        udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:33434 
LSI        icmp --  0.0.0.0/0            0.0.0.0/0           
DROP       all  --  0.0.0.0/0            255.255.255.255     
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
LSI        all  -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
INBOUND    all  --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
LSI        udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:33434 
LSI        icmp --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (6 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
LOG        icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  41.208.218.186       196.30.31.193       tcp dpt:53 
ACCEPT     udp  --  41.208.218.186       196.30.31.193       udp dpt:53 
ACCEPT     tcp  --  41.208.218.186       196.46.70.1         tcp dpt:53 
ACCEPT     udp  --  41.208.218.186       196.46.70.1         udp dpt:53 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output'[/FONT]
```
PS the rules were automatically generated when I configured pppoe.

---

### Post by pavel_kbc on 2006-12-06
when firestarter is runing i cant connect to anything . plesae help me

---

### Post by Wim Sturkenboom on 2006-12-07
wrong button

---

### Post by pavel_kbc on 2006-12-07
whatever . i uninstalled firestarter :P

---

### Post by Wim Sturkenboom on 2006-12-07
Issue the command *sudo iptables -L -n* when connected to the internet. If you get output like posted above, the firewall rules are applied. If it's only a few lines like ```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination 
```, no firewall rules are applied.

PS 'can not connect to anything' is not very clear. I suppose that you're talking about websites and email servers, but it just as well could have been referring to your local network only.

---

### Post by yy1124 on 2006-12-07
not very sure of what pavel_kbc refers to...

but for my case I do meant websites, at least thats the service I noticed so far that stops after I click the "activate" button of firestarter...

---

### Post by Wim Sturkenboom on 2006-12-07
OK, so it blocks too much.

_step 1_
Try in a terminal to ping i.e. [www.google.com](www.google.com) while the firewall is activated. Interrupt it after a few seconds with <ctrl>C (control-c)

It will more than likely fail, but it's important to know how it fails
```
wim@internet-desktop:~$ ping www.google.com
PING www.l.google.com (***216.239.59.103***) 56(84) bytes of data.

--- www.l.google.com ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms
```Above comes from my machine with the firewall on. Important is that I see the IP address so I know that the name is translated to an ip address by the DNS server.
If you don't see it the ip address, the problem is in the name resolving.

_step 2_
If you get an ip address, try [http://216.239.59.103/](http://216.239.59.103/) in the address bar of your browser (replace the ip address by what you found). It should take you to google (or the site that you checked).
If not, http (port 80) is blocked.

Just let me know where it fails. I'm absolutely no specialist with iptables, but will try to help as I want to figure out how it works in Ubuntu (I know more or less how it works in slackware).

PS please post the output of *sudo iptables -L -n* and *ifconfig* (for the same internet session)

---

### Post by pavel_kbc on 2006-12-08
i meant to say . i cannot connect to anything "irc , mail server , ping and all other without 80 port"

---

### Post by pavel_kbc on 2006-12-08
whatever i dont need help with firestarter anymore (coz i uninstalled it :D ) :) thank you everyone

---

### Post by yy1124 on 2006-12-09
Sorry for the late reply,
I have to reinstall Ubuntu for some reason >.<.

I appreciate you help very much.

> **Wim Sturkenboom said:**
> OK, so it blocks too much.

_step 1_
Try in a terminal to ping i.e. [www.google.com](www.google.com) while the firewall is activated. Interrupt it after a few seconds with <ctrl>C (control-c)



ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (64.233.189.104) 56(84) bytes of data.
64 bytes from 64.233.189.104: icmp_seq=1 ttl=245 time=51.0 ms
64 bytes from 64.233.189.104: icmp_seq=2 ttl=245 time=49.8 ms
64 bytes from 64.233.189.104: icmp_seq=3 ttl=245 time=50.8 ms
64 bytes from 64.233.189.104: icmp_seq=4 ttl=245 time=49.5 ms
64 bytes from 64.233.189.104: icmp_seq=5 ttl=245 time=49.7 ms
64 bytes from 64.233.189.104: icmp_seq=6 ttl=245 time=49.8 ms
64 bytes from 64.233.189.104: icmp_seq=7 ttl=245 time=50.6 ms
64 bytes from 64.233.189.104: icmp_seq=8 ttl=245 time=50.6 ms
64 bytes from 64.233.189.104: icmp_seq=9 ttl=245 time=50.6 ms

The funny thing is my pc seems to receive the packets...


> **Wim Sturkenboom said:**
> 
_step 2_
If you get an ip address, try [http://216.239.59.103/](http://216.239.59.103/) in the address bar of your browser (replace the ip address by what you found). It should take you to google (or the site that you checked).
If not, http (port 80) is blocked.

Just let me know where it fails. I'm absolutely no specialist with iptables, but will try to help as I want to figure out how it works in Ubuntu (I know more or less how it works in slackware).

PS please post the output of *sudo iptables -L -n* and *ifconfig* (for the same internet session)

My IPtables:
```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  202.188.0.*        0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  202.188.0.*       0.0.0.0/0           
ACCEPT     tcp  --  202.188.1.5          0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  202.188.1.5          0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
DROP       all  --  0.0.0.0/0            255.255.255.255     
DROP       all  --  0.0.0.0/0            60.48.250.166       
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
LSI        all  -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
INBOUND    all  --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  60.48.*.*        202.188.0.*       tcp dpt:53 
ACCEPT     udp  --  60.48.*.*        202.188.0.*       udp dpt:53 
ACCEPT     tcp  --  60.48.*.*        202.188.1.*         tcp dpt:53 
ACCEPT     udp  --  60.48.*.*        202.188.1.*         udp dpt:53 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:80 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpts:6881:6889 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:6881:6889 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpts:67:68 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:67:68 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpts:20:21 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:20:21 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:443 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:143 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:143 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:111 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:111 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:2049 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:2049 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:119 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:119 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:123 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:123 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:110 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:110 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpts:137:139 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:137:139 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:445 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:25 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:25 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:22 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:23 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:23 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpts:6000:6015 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:6000:6015 
LSI        all  --  0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
LOG        icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0   

```

and my ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:11:09:8C:D4:D4  
          inet addr:60.48.*.*  Bcast:60.48.*.*  Mask:255.255.255.255
          inet6 addr: fe80::211:9ff:fe8c:d4d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10802200 (10.3 MiB)  TX bytes:652363 (637.0 KiB)
          Interrupt:185 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:11:09:8C:D4:D5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

```

Thanks.

---

### Post by yy1124 on 2006-12-09
WIll keep trying >.<

---

