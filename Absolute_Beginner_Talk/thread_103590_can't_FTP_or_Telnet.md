---
title: "can't FTP or Telnet"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by NoBullMan on 2005-12-14
Hi,
I have just finished setting up a web server, using the "Perfect Setup for Ubuntu 5.10" document from [www.howtoforge.com](www.howtoforge.com). 
My server is behind a Linksys router. In the router I have forwarded ports 21 (FTP) and 23 (Telnet) to the server's local IP of 192.168.0.10.
When I use a Windows PC to ftp to the server (using WS-FTP), the connection times out. Same thing with telnet. The services are running on the server. I even enabled UPnP and forwarded the FTP and Telnet ports to 192.168.0.10, but it still doesn't work. I tried from a laptop that is on the same network as he server and used the local IP, instead of WAN IP, same thing.

Can someone tell me what I need to do to get the ftp service working?

Thanks.

---

### Post by lreyes6 on 2005-12-14
first of all thanks for the guide will be a lot of help for me... i was wondering for something like that jeje...

now back to your question... you can start/stop/restart your proftp service from the command line like this
```
sudo /etc/init.d/proftpd start
```

you just change the start word on the line for the command u want (stop, restart)

and that is for any service that you have under the /etc/init.d/ directory...

hope this help

---

### Post by localzuk on 2005-12-14
Further to this it is always useful to know what ports are open on your machine. To do this try using the program nmap.

A simple execution of nmap that lists open ports would be:

```

nmap -sS -v -O 192.168.0.10

```

That will produce something like:

```

[root@machine workshop]# nmap -sS -v -O 127.0.0.1

Starting nmap 3.81 ( http://www.insecure.org/nmap/ ) at 2005-12-14 17:08 GMT
Initiating SYN Stealth Scan against localhost.localdomain (127.0.0.1) [1663 ports] at 17:08
Discovered open port 22/tcp on 127.0.0.1
Discovered open port 25/tcp on 127.0.0.1
Discovered open port 80/tcp on 127.0.0.1
Discovered open port 631/tcp on 127.0.0.1
Discovered open port 3306/tcp on 127.0.0.1
Discovered open port 111/tcp on 127.0.0.1
The SYN Stealth Scan took 0.32s to scan 1663 total ports.
For OSScan assuming port 22 is open, 1 is closed, and neither are firewalled
Host localhost.localdomain (127.0.0.1) appears to be up ... good.
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1657 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
111/tcp  open  rpcbind
631/tcp  open  ipp
3306/tcp open  mysql
Device type: general purpose
Running: Linux 2.4.X|2.5.X|2.6.X
OS details: Linux 2.4.0 - 2.5.20, Linux 2.5.25 - 2.6.3 or Gentoo 1.2 Linux 2.4.19 rc1-rc7), Linux 2.6.3 - 2.6.8
TCP Sequence Prediction: Class=random positive increments
                         Difficulty=3056766 (Good luck!)
IPID Sequence Generation: All zeros

Nmap finished: 1 IP address (1 host up) scanned in 2.842 seconds
               Raw packets sent: 1679 (67.4KB) | Rcvd: 3369 (136KB)

```

So from this you can see that services are running on a set of ports.

---

### Post by NoBullMan on 2005-12-14
Thank you guys,
I restarted the service but it didn't help.

I ran nmap but all I got was:

nmap version 3.81 ( [http://www.insecure.org/nmap](http://www.insecure.org/nmap) )

Nothing else!

---

### Post by NoBullMan on 2005-12-14
I just stopped Norton Internet Security and now I am getting a different error message. It does not time out, but the log displays:

connection to 192.168.0.10:32776
connected to 192.168.0.10 port 32776
LIST
! Receive error: Blocking call cancelled
! Retrieve of folder listing failed [4]

I used the WAN IP address when trying to FTP, yet the log shows the LAN IP address.

---

### Post by localzuk on 2005-12-16
Have you got a firewall enabled on your ubuntu machine?

---

