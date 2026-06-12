---
title: "Am I compromised?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Paul_world10 on 2007-09-04
Hi, can someone tell me if I should worry about this netstat output? Establishing a connection on 

localhost:43137
                               --should concern me?
localhost:39181

Heres my command output

[HTML]paul@desktopbox:~$ netstat -t
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost:39181         localhost:43137         ESTABLISHED
tcp        0      0 192.168.1.5:39971       ohiggins.ubuntu.com:www TIME_WAIT
tcp        0      0 192.168.1.5:39969       ohiggins.ubuntu.com:www TIME_WAIT
tcp        0      0 192.168.1.5:39973       ohiggins.ubuntu.com:www TIME_WAIT
tcp        0      0 192.168.1.5:50284       ro-in-f99.google.co:www ESTABLISHED
tcp        0      0 192.168.1.5:50030       83.125.32.58:9001       ESTABLISHED
tcp        0      0 localhost:43137         localhost:39181         ESTABLISHED


paul@desktopbox:~$ sudo netstat -tupan
Password:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State PID/Program name
tcp        0      0 127.0.0.1:39181         0.0.0.0:*               LISTEN     4508/hpiod
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN     5219/privoxy
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4582/cupsd
tcp        0      0 127.0.0.1:58072         0.0.0.0:*               LISTEN     4535/python
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     4624/exim4
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN     4826/tor
tcp        0      0 127.0.0.1:39181         127.0.0.1:43137         ESTABLISHED4508/hpiod
tcp        0      0 192.168.1.5:50030       83.125.32.58:9001       ESTABLISHED4826/tor
tcp        0      0 127.0.0.1:43137         127.0.0.1:39181         ESTABLISHED4535/python
tcp6       0      0 :::25                   :::*                    LISTEN     4624/exim4
udp        0      0 0.0.0.0:68              0.0.0.0:*                          4516/dhclient3
[/HTML

Thank you in advance.

---

### Post by mlentink on 2007-09-04
Do you happen to have a HP printer installed? hpiod looks like a HP-printer related process.

As far as I can see, it concerns local processes, so I don't think you're compromised. 
But undoubtedly there are better minds here who could say definitively.

---

### Post by Paul_world10 on 2007-09-04
Thank you for your response, I have no HP printer installed but do have the HP toolkit package installed. Firestarter isn't showing anything out of the ordinary whatsoever either. 

I am continually getting inbound 1.3 and outbound .28 in my system->monitor->network history though.

a port scan at [www.grc.com](www.grc.com) continually shows all stealth.

i'll keep looking into it I guess.

---

### Post by Tiger-Smith on 2007-09-04
HP Input Output Device "hpiod", as far as I'm aware the other ports are out of normal application ranges and are just on the loopback so nothing to worry about, its used so services can communicate between each other.

---

