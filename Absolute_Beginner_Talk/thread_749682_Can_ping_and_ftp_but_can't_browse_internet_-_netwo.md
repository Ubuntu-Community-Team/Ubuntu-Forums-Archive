---
title: "Can ping and ftp but can't browse internet - network settings?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by shano1977 on 2008-04-08
Hi, I'm new to Ubuntu Linux, having just installed 7.10 a few days ago.  I'm hoping someone is able to help me with my network settings to enable me to browse the internet.  

For some background, my PC has 2 hard drives with ubuntu installed on a partition of the second drive.  Windows XP is on the first drive and I can boot into either windows or linux at startup.

I have an voip router connected to an adsl modem which is connected to the internet.  The PC connects into the voip router via ethernet cable and the adsl modem is set up in "bridge" mode.  In windows my LAN settings are set to obtain IP and DNS server addresses automatically.  In windows I was able to type the IP address of the voip router (192.168.30.1) into the firefox browser and see the device status and setup etc.  

I'm trying to set up ubuntu to enable me to browse the internet with firefox (as per windows), but have been unsuccessful.  The symptoms are as follows:
- I can ping the voip router (192.168.30.1) from the command line, but when I type this IP address in firefox nothing comes up (seems to just search forever with blank browser screen)
- I can ping web-sites from the command line, but can't see them in web browser (for example, firefox status bar will show "Looking up... ebay.com", then  "Waiting for...  ebay.com"  but nothing further).
- I can ftp sites from command line and download files.

I'm guessing I've got some things wrong in the "Network Settings" GUI.  The tabs in this GUI are:
- Connections tab: Wired connection Address dhcp (automatic).  I assume this is ok?
- General tab: not sure what to put for "host name" or "domain name", I've left the host name as the default which is the name of my machine
- DNS servers tab: "DNS servers", "search domains". Not sure what needs to go in here if any. I've left it as the default DNS server of 192.168.30.1 and 0.0.0.0.  No search domains at present.
Hosts tab: There is a default list of IP addresses and aliases.  Not sure if I need to do anything here?


If it helps here is some more information on my configuration:

From ifconfig:
eth0   Link encap:Ethernet  HWaddr 00:01:03:41:77:1C  
          inet addr:192.168.30.2  Bcast:192.168.30.255  Mask:255.255.255.0
          inet6 addr: fe80::201:3ff:fe41:771c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6539 (6.3 KB)  TX bytes:12590 (12.2 KB)
          Interrupt:3 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX pakets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1636 (1.5 KB)  TX bytes:1636 (1.5 KB)

From "/etc/hosts":
# The following lines are desirable for IPv6 capable hosts
ff00::0 ip6-mcastprefix
127.0.0.1 localhost
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
::1 ip6-localhost ip6-loopback
127.0.1.1 mycomputername
ff02::3 ip6-allhosts

Can anyone see where I'm going wrong?  Still have been unable to browse the internet.

Thanks.

---

### Post by Oldsoldier2003 on 2008-04-08
> **shano1977 said:**
> 

I'm guessing I've got some things wrong in the "Network Settings" GUI.  The tabs in this GUI are:
- Connections tab: Wired connection Address dhcp (automatic).  I assume this is ok?
- General tab: not sure what to put for "host name" or "domain name", I've left the host name as the default which is the name of my machine
- DNS servers tab: "DNS servers", "search domains". Not sure what needs to go in here if any. I've left it as the default DNS server of 192.168.30.1 and 0.0.0.0.  No search domains at present.
Hosts tab: There is a default list of IP addresses and aliases.  Not sure if I need to do anything here?


If it helps here is some more information on my configuration:

From ifconfig:
eth0   Link encap:Ethernet  HWaddr 00:01:03:41:77:1C  
          inet addr:192.168.30.2  Bcast:192.168.30.255  Mask:255.255.255.0
          inet6 addr: fe80::201:3ff:fe41:771c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6539 (6.3 KB)  TX bytes:12590 (12.2 KB)
          Interrupt:3 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX pakets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1636 (1.5 KB)  TX bytes:1636 (1.5 KB)

From "/etc/hosts":
# The following lines are desirable for IPv6 capable hosts
ff00::0 ip6-mcastprefix
127.0.0.1 localhost
fe00::0 ip6-localnet
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
::1 ip6-localhost ip6-loopback
127.0.1.1 mycomputername
ff02::3 ip6-allhosts

Can anyone see where I'm going wrong?  Still have been unable to browse the internet.

Thanks.

edit sorry misread a couple things. That is not a valid DNS server, ubless your voip router runs dns service (which is highly doubtful)

NetRange:   192.168.0.0 - 192.168.255.255 
CIDR:       192.168.0.0/16 
NetName:    IANA-CBLK1
NetHandle:  NET-192-168-0-0-1
Parent:     NET-192-0-0-0-0
NetType:    IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
Comment:    This block is reserved for special purposes.
Comment:    Please see RFC 1918 for additional information.
Comment:    [http://www.arin.net/reference/rfc/rfc1918.txt](http://www.arin.net/reference/rfc/rfc1918.txt)
RegDate:    1994-03-15
Updated:    2007-11-27






 when you say you can ping or ftp are you usining ipaddress or hostnames? if you have connectivity ip addresses will always work.

---

### Post by Whiffle on 2008-04-08
Try another web browser, if that works, clear the DNS cache in firefox by putting it into "offline mode" and then not in online mode.

---

### Post by shano1977 on 2008-04-08
ok.  Should I just remove all entries under DNS servers?  I think I tried this on a previous occasion but "Problem loading page" came up and firefox showed "server not found"

---

### Post by pseudo-random on 2008-04-08
check your DNS from the terminal with something like ```
nslookup google.com
```
If it returns an error you need to sort out your DNS server in the network GUI or edit /etc/resolv.conf
Are you pinging these websites by name or IP?
If its name then the next step I would suggest would be to netcat to the webserver to test your connection.
```
nc -v google.com 80
```
Then issue a GET to illicit a response:
```
GET pagethatdoesnotexist.html
```
If you get a load of HTML back your problem is all in firefox.

---

### Post by Oldsoldier2003 on 2008-04-08
> **shano1977 said:**
> ok.  Should I just remove all entries under DNS servers?  I think I tried this on a previous occasion but "Problem loading page" came up and firefox showed "server not found"

in your windows box do ipconfig /all of is it ipcfg /all? been so long I barely remember. Anyhow write down your dns server settings from windows and plug them into ubuntu.

---

### Post by shano1977 on 2008-04-08
I tried "w3m" but same thing as firefox ie "website found..." then "waiting for www.ebay.com.au" or something similar.

Are my Network Settings GUI fields ok?

---

### Post by shano1977 on 2008-04-08
Thanks for all the replies.  I'll try some of your suggestions when I get home.
ie .windows "ipconfig", "nslookup" and "nc"

---

### Post by shano1977 on 2008-04-08
deleted

---

### Post by shano1977 on 2008-04-08
> **Oldsoldier2003 said:**
> edit sorry misread a couple things. That is not a valid DNS server, ubless your voip router runs dns service (which is highly doubtful)

 when you say you can ping or ftp are you usining ipaddress or hostnames? if you have connectivity ip addresses will always work.

Pretty sure the voip router doesn't run dns service

I've been able to ping ip addresses and hostnames.  
Haven't tried ftp'ing an IP address but have ftp'd to a hostname eg "web.netcall.com.au"

Would I need to change anything in the hosts tab?

---

### Post by shano1977 on 2008-04-14
Seems my router was the problem as per this thread:
[http://ubuntuforums.org/showthread.php?t=418144](http://ubuntuforums.org/showthread.php?t=418144)

Adding a setting to  "/etc/sysctl.conf" solved the problem for me.
ie added line "net.ipv4.tcp_default_window_scaling = 0".

---

### Post by bombastic on 2008-06-27
> **shano1977 said:**
> Adding a setting to  "/etc/sysctl.conf" solved the problem for me.
ie added line "net.ipv4.tcp_default_window_scaling = 0".
Wow thanks... I've been searching for like 4 hours and finally found a solution which works!

---

