---
title: "Problem with network printing"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by the-nuke on 2008-03-18
Hi
this is my setup
laptop 192.168.0.3 connected to Netgear wireless router 193.168.0.1. I have a netgear wireless print server  192.168.0.5  connected  to router. The print server has a HP PSC1317 connected

This my problem, Set up using cups and it went great, setup printed no problem. the problem in that i can't print the following day after laptop rebooted
the cupsd.conf file show the following
LogLevel warning
SystemGroup lpadmin
# Only listen for connections from the local machine.
Listen 631
Listen /var/run/cups/cups.sock
# Disable printer sharing and shared printers.
Browsing On
DefaultAuthType Basic
<Location />
  # Restrict access to the server...
  Order allow,deny
  Allow localhost
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
  Allow localhost
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
  Allow localhost
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

hopefully this is an easy fix. been using ubuntu for a month and think it is great even though i can't get sound to work. Hopefully  will get sorted with Hardy

---

### Post by handydan918 on 2008-03-18
You know, the first thing that comes to mind is to make sure that after the reboot cups is still running. If you do top or ps -ax in a terminal, do you see cupsd listed?

---

### Post by the-nuke on 2008-03-18
Sorry for the delay in the reply, had to go to work.
done what you suggested and no i cannot see it running. How do I get it running on re-boot

thanks

---

### Post by handydan918 on 2008-03-18
System>Administration>Services
check the box by cupsd...

---

### Post by the-nuke on 2008-03-18
thanks for the reply, This was already checked. I suspect cups is starting.
But still no printing. Print server has a static ip 192.168.0.5 if this helps. I need to be able to print, so this is driving me up the wall

when i try to print test page via the cups interface i get network busy retry in 30secs

thanks

---

### Post by handydan918 on 2008-03-18
Just for fun, install nmap and do ```
nmap 192.168.0/27
```
Let's see who's out there and on what ports...

---

### Post by the-nuke on 2008-03-19
did as you suggested and this is what came up

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-03-19 08:52 GMT
Interesting ports on 192.168.0.1:
Not shown: 1712 closed ports
PORT     STATE SERVICE
80/tcp   open  http
5190/tcp open  aol

Interesting ports on 192.168.0.3:
Not shown: 1713 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap done: 32 IP addresses (2 hosts up) scanned in 2.529 seconds
as you can see 192.168.0.5 doesn't seem to be there. I can print on the same machine via vista.

---

### Post by handydan918 on 2008-03-19
> **the-nuke said:**
> did as you suggested and this is what came up

Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-03-19 08:52 GMT
Interesting ports on 192.168.0.1:
Not shown: 1712 closed ports
PORT     STATE SERVICE
80/tcp   open  http
5190/tcp open  aol

This is interesting...why do you have port 80 open? Hmmm...Nothing to do with printing.


Interesting ports on 192.168.0.3:
Not shown: 1713 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

This really looks like a printer to me. 
If you are behind a router, it's probably doing dhcp and re-assigning IP's to the various machines. I would try setting the router to "reserve" an address to each device, so that the IP's aren't changing all the time.> 
Nmap done: 32 IP addresses (2 hosts up) scanned in 2.529 seconds
as you can see 192.168.0.5 doesn't seem to be there. I can print on the same machine via vista.
Well that's interesting, but what do you mean "the same machine"?
Can Vista see something at 192.168.0.5 that nobody else can?

---

### Post by the-nuke on 2008-03-19
Right gents

just an update, went into Vista and was having problems with printing also. Went to admin page of router and noticed that under attached devices nothing was showing, even though the laptop was connected. Anyway updated firmware and all attached devices were seen. Now printing vista and Ubuntu at the moment.
with regards to port 80 you have me worried, can you expand a little

---

### Post by handydan918 on 2008-03-19
Port 80 is accepting http traffic. Unless you have a webserver running, I don't think that should be the case. If you are behind a NAT router, I wouldn't sweat it, tho.
If you want to do a good port scan on yourself, go to [www.grc.com](www.grc.com) and run the Shields Up! test.

---

