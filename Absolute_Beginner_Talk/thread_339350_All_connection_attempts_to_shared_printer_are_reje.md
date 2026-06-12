---
title: "All connection attempts to shared printer are rejected"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-01-15
Since my "shared printing died" I have been trying to correct the problem.

I have been able to reopen port 631 -- but as of yet cannot connect.

I was using the help file at [https://help.ubuntu.com/community/NetworkPrintingFromWin2000](https://help.ubuntu.com/community/NetworkPrintingFromWin2000)

Previously I successfully set up printer sharing using the IP of 192.168.1.2 -- but this now seemingly does not work.

When I go to System>Administration>Networking I find that my DNS server is set up as 192.168.1.1.
 I find the localhost IP is set up as 127.0.0.1 and my own desktop as a.127.0.1.1.  However when I input these IP settings into the WIN 2000 computer in the URL (for network printer set-up) -- it does not find anything and returns the error message: "Could not connect to the printer. You either entered a printer name that was incorrect or the specified printer is no longer connected to the server."

Droppinig the IP address and simply using my "computer's name" returns the same results.

Below I am including my cupsd.conf file 

My printer is a Brother HL-5140 (this is not a network printer); I am running Ubuntu 6.10

If you find any errors please be real specific on the error and needed correction-- I'm still feeling my way through Linux as a newbie of just a little more than an week old. . .

-----------------------------------------------------------
#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
Listen 127.0.0.1:631
Listen /var/run/cups/cups.sock
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder deny, allow
BrowseAllow @LOCAL
BrowseAddress 192.168.1.*

Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
BrowseAddress 192.168.1.*
     
<Location />
AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL
Allow From 192.168.1.*
</Location>
    
<Location /jobs>
AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL
Allow From 192.168.1.*
</Location>
    
<Location /printers>
AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL
Allow From 192.168.1.*
</Location>

<Location /admin>
AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL
Allow From 192.168.1.*
</Location>



# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
---------------------------------------------

---

### Post by steve.horsley on 2007-01-15
I'm not familiar with cips configuration, but at a quick look, this may be the problem:
> # Only listen for connections from the local machine.
Listen 127.0.0.1:631
Listen /var/run/cups/cups.sock
Listen localhost:631
Listen /var/run/cups/cups.sock

127.0.0.1 (and localhost, whic is the name for that address) is the address that only the local machine can connect to. If cups is only listening on that address, that is probably your problem. I don't know what the correct setting is, but you could try **listen 0.0.0.0** instead.

---

### Post by chaplanger on 2007-01-16
> **steve.horsley said:**
> I'm not familiar with cips configuration, but at a quick look, this may be the problem:

127.0.0.1 (and localhost, whic is the name for that address) is the address that only the local machine can connect to. If cups is only listening on that address, that is probably your problem. I don't know what the correct setting is, but you could try **listen 0.0.0.0** instead.

I've remarked out the lines referencing 127.0.0.1 -- Though I can still print on my local machine, still not able to share the printer.  BTW -- Global Settings now shows that "Share Printers" is the default.

---

### Post by steve.horsley on 2007-01-17
Let's make sure. Can you run the command **netstat -lntu** and see what address is listening on 631?

---

### Post by chaplanger on 2007-01-17
> **steve.horsley said:**
> Let's make sure. Can you run the command **netstat -lntu** and see what address is listening on 631?

Thanks for the idea -- below are the results -- i simply don't know how to interpret them though. .  .so can you tell me what you see here? (and what I should do)
-----------------------------
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:902             0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:44392         0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp6       0      0 :::631                  :::*                    LISTEN     
udp        0      0 172.16.230.1:137        0.0.0.0:*                          
udp        0      0 192.168.195.1:137       0.0.0.0:*                          
udp        0      0 192.168.1.4:137         0.0.0.0:*                          
udp        0      0 0.0.0.0:137             0.0.0.0:*                          
udp        0      0 172.16.230.1:138        0.0.0.0:*                          
udp        0      0 192.168.195.1:138       0.0.0.0:*                          
udp        0      0 192.168.1.4:138         0.0.0.0:*                          
udp        0      0 0.0.0.0:138             0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:631             0.0.0.0:*     
--------------------------------

Thanks for helping this newbie!

---

### Post by steve.horsley on 2007-01-18
There are 3 lines showing usage of port 631:
**tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN **
This is the problem. TCP is listening on 127.0.0.1 which is the PCs internal loopback address. You need to get it to listen on 0.0.0.0 (all addresses the machine has) or its LAN address somehow. 

**tcp6 0 0 :::631 :::* LISTEN **
It's listening on all network interfaces for TCP/IPv6 connections. It's not likely that you will use this protocol.

**udp 0 0 0.0.0.0:631 0.0.0.0:* **
It's also listening on all interfaces for UDP packets. But I think TCP is what you need, and as I said above, that's the problem.

---

### Post by chaplanger on 2007-01-18
> **steve.horsley said:**
> There are 3 lines showing usage of port 631:
**tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN **
This is the problem. TCP is listening on 127.0.0.1 which is the PCs internal loopback address. You need to get it to listen on 0.0.0.0 (all addresses the machine has) or its LAN address somehow. 

**tcp6 0 0 :::631 :::* LISTEN **
It's listening on all network interfaces for TCP/IPv6 connections. It's not likely that you will use this protocol.

**udp 0 0 0.0.0.0:631 0.0.0.0:* **
It's also listening on all interfaces for UDP packets. But I think TCP is what you need, and as I said above, that's the problem.


To clarify: I have now edited my cupsd.conf  file:  

```
# Only listen for connections from the local machine.
Listen 127.0.0.1:631
Listen /var/run/cups/cups.sock
Listen localhost:631
Listen /var/run/cups/cups.sock 
```

to:

```
# Only listen for connections from the local machine.
# Listen 127.0.0.1:631
# Listen /var/run/cups/cups.sock
Listen 0.0.0.0 
Listen /var/run/cups/cups.sock

```

After this I ran
```
netstart -intu
```

and received this information:

```
david@david-desktop:~$ sudo gedit  /etc /cups/cupsd.conf
Password:
david@david-desktop:~$ sudo gedit /etc/cups/cupsd.conf
david@david-desktop:~$ sudo /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd                         [ ok ] 
david@david-desktop:~$ netstat -lntu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:2208                 0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:902                      0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:44392               0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139                      0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:631                      0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445                      0.0.0.0:*               LISTEN     
tcp6       0      0 :::631                               :::*                    LISTEN     
udp        0      0 172.16.230.1:137            0.0.0.0:*                          
udp        0      0 192.168.195.1:137          0.0.0.0:*                          
udp        0      0 192.168.1.4:137              0.0.0.0:*                          
udp        0      0 0.0.0.0:137                     0.0.0.0:*                          
udp        0      0 172.16.230.1:138            0.0.0.0:*                          
udp        0      0 192.168.195.1:138          0.0.0.0:*                          
udp        0      0 192.168.1.4:138              0.0.0.0:*                          
udp        0      0 0.0.0.0:138                     0.0.0.0:*                          
udp        0      0 0.0.0.0:68                       0.0.0.0:*                          
udp        0      0 0.0.0.0:631                     0.0.0.0:*                          
david@david-desktop:~$ 
```

Still though I am not getting the WIN 2000 machine to see this printer.

I am still confused as to what IP address I use to set up the shared printing?  How do I find this IP address.  (Maybe this is my error now?)

I am using the following code to set up my shared printing:

```
http://IPAddress:631/printers/HL-5140
```

I have also substituted the name: "david-desktop:631" for the IP portion and still nothing. . . 

As If you can't tell, I am still quite new to Linux/Ubuntu, and need a bit of hand-holding here to make certain I get this right.

---

### Post by steve.horsley on 2007-01-19
I can see that it's listening properly now. You should be able to telnet to port 631 from the win2k box and have the call accepted now. Beyond this, I'm afraid I can't help - I've never configured printing from windows.

---

### Post by Xappe on 2007-01-19
I would change the listening part in cupsd.conf to:

Listen 631

and then make sure the win2k machine is allowed to access cupsd (look further down the file):

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow <win2k ip>	
  Allow @LOCAL
</Location>

---

### Post by chaplanger on 2007-01-21
> **Xappe said:**
> I would change the listening part in cupsd.conf to:

Listen 631

and then make sure the win2k machine is allowed to access cupsd (look further down the file):

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow <win2k ip>	
  Allow @LOCAL
</Location>

Xappe,
Alright -- I have now added Listen 631 to cupsd.conf

Where do I find the IP address needed for the WIN box?

Also where can I identify my IP address for my Linux machine?

Thanks for any further assistance -- 
Thanks to Steve.horsley for your help up to this point!

---

### Post by wpshooter on 2007-01-21
I hope you good luck with this problem.

I have (for now) given up on getting my printer shared under Ubuntu.

Sharing a printer should just not be this difficult, it isn't under M/S windows !!!

They really need to do some programing to get this to work without the user having to reinvent the wheel.

Good luck.

---

### Post by Xappe on 2007-01-21
in windows: start -> run... -> cmd -> ipconfig
in ubuntu: open up a terminal and type ifconfig

make sure you can ping the ubuntu box from windows

ping <ubuntu box ip> (from windows commandline)

---

### Post by chaplanger on 2007-01-23
> **Xappe said:**
> in windows: start -> run... -> cmd -> ipconfig
in ubuntu: open up a terminal and type ifconfig

make sure you can ping the ubuntu box from windows

ping <ubuntu box ip> (from windows commandline)

As previously mentioned -- I need help in identifying my machines IP address:

Where is my machine's IP adddress located?
If it is in a config file, Exactly what lines of code am I looking for?

I keep finding too many potential IP addresses (local machine et al) and am confused.

---

### Post by bcom on 2007-01-23
I take it that the printer you want to share is attached to the machine running Ubuntu.  

If that is the case and you are trying to connect to it from a windows machine then you need to enter the IP address of the Ubuntu computer that you want to connect to on the Windows machine.

If you enter 127.0.0.0 or 127.0.0.1 on the Windows computer, you are telling the Windows computer to look to itself for the printer.  

127.0.0.1 is always a loopback address; it refers to the local computer; you cannot use this address to connect to any other computer on a network.

The IP address that you want to enter on the Win2000 machine is the IP address given to the Ubuntu box by the DHCP server (which is most probably your router).  Just looking at some of the output you have posted that address might be 192.168.1.4.

To get the IP address that you need: On the Ubuntu box open up a Terminal and enter ifconfig.  Your output should look something like this:

eth0      Link encap:Ethernet  HWaddr 00:03:47:D6:2D:4F  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0

The address from the Ubuntu box you need to enter on the Windows computer to access the computer attached to Ubuntu would be 192.168.1.x.

---

### Post by chaplanger on 2007-01-29
bcom,
Thanks for your help!

I was out of town for a few days -- your help in identifying the ip port was spot on!  My WIN2000 box can now print through my Linux machine.

Thanks to Steve.horsley and xappe for all of your help in getting the "cupsd.conf" file corrected and all of your assistance!

Joy is restored.

---

