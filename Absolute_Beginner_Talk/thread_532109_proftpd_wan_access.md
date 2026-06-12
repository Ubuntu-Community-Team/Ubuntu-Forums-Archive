---
title: "proftpd wan access"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by paulow1978 on 2007-08-22
Hi All,

I am tryig to set up a proftpd server. SO far....

installed it and can access it when the server is on the same internal ip address. However, we need this machine to be in the dmz so we can put files on for outside companies, as well as being able to access it internally. I have set up the firewall to allow all this. I can ping from internal to dmz ubuntu server. I can ping from ubuntu to internal. The ip address of the ubununtu machine has a public ip address in the dmz. However I cannot access it via ftp from internal or external ips... (I checked the firewall logs and the packets are being allowed through to the dmz). Is there a config file that you can say "allow access from ip addresses not on the same subnet" or something? similarly I am having exactly the same problem using vnc..... any help would greatly greatly appreciated...

many thanks!

Paul
:lolflag:

---

### Post by HermanAB on 2007-08-23
Uhmmm...  You say that the firewall DMZ is configured to forward all incoming traffic to your router public IP address to the private LAN IP address of the computer?

What does 'sudo ipconfig' say?

What does 'sudo route' say?  Is the default gateway configured to point to the gateway address supplied by your ISP?

Can you 'sudo ping [www.yahoo.com](www.yahoo.com)' ?

Cheers,

Herman

---

### Post by HermanAB on 2007-08-23
Please describe your system complete with all IP addresses so we can discuss it properly.

Cheers,

H.

---

### Post by paulow1978 on 2007-08-23
Hi,

sorry If I wasn't clear enough in my first post.

Basically I have one ubuntu machine configured with a public ip address of

195.x.x.x/29

(we have 8 public ip addresses available for our company hence the /29)

The firewall has an external address of 195.x.x.x/29 and an internal address of 128.1.x.x/16

I have put the ubuntu machine into the dmz of the firewall. I have allowed access from 128.1.x.x to the dmz for all ports. I have allowed ftp access from external (i.e. the internet) to the dmz.

If I put the ubuntu machine on a 128.1.x.x address and plug it in to the internal network I can ftp into it from a pc. If I set it up as above I cannot get access to it even though when I check the firewall logs it is allowing the ftp packets to pass through to the dmz to the ubuntu machine. Its as if the ubuntu machine won't allow connections from machines on a different subnet.

any help would be greatly appreciated

thanks,

Paul

---

### Post by HermanAB on 2007-08-23
OK, Linux has a packet filter in the kernel, called netfilter.  Netfilter can be controlled by a program called iptables.  It is possible that netfilter is dropping the packets, so flush all netfilter rules, then try again.

First see what rules are set:
$ sudo iptables -L

Then reset all:
$ sudo iptables -F

You can install the packet sniffer tcpdump and look at the incoming packets:
$ sudo tcpdump -A -s 256 -i eth0

---

