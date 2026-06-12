---
title: "Where is my server IP address"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-09-18
The instructions below will hopefully allow me to use my printer with both Ubuntu desktop computers. At present one is connected and working on my main PC. Having followed these instructions I now need to locate my  servers ip address to complete this part of the instructions

"ipp://192.168.0.1/printers/<name of printer"

where would I find this ip adress please.

*********************************************************************************************

On the server machine (the one the printer is attached to) open up printer manager with 
sudo gnome-cups-manager 
    

or System->Administration->Printing. 

Under Global Settings click on the share printers. 
Ubuntu Client Machine

Now on the client(s) open up the printer manager System->Administration->Printing and under the Global Settings check the Detect LAN Printers option.Then go to Printer->Add Printer check the Network Printer option and in the area marked URI write something like 

ipp://192.168.0.1/printers/<name of printer> 

where 192.168.0.1 is your servers ip address and <name of printer> is the name you gave the printer when you set it up (usually the model of the printer). Click Next and select the brand,model, and driver just like you did when setting up the printer on the server. Click Next and fill in the name and description like on the server's printer then click Next. There you should now have a networked printer.

***********************************************************************************

---

### Post by cmnorton on 2007-09-18
ping the server by name or log into the server, create an xterm, and enter the ifconfig command.

If neither of these work, whomever set up the server would know its ip address.

---

### Post by a.v.l on 2007-09-18
> **cmnorton said:**
> ping the server by name or log into the server, create an xterm, and enter the ifconfig command.

If neither of these work, whomever set up the server would know its ip address.

I'm afraid I didn't understand any of your instruction.

Can you explain in more detail please  i.e. something a beginner will understand?

---

### Post by qpieus on 2007-09-18
At the server computer, open up a terminal window and type

ifconfig

you'll get a response in the terminal window that looks something like this:

```
gdfgghh@server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 44:44:44:4C:54D:24
          inet addr:192.168.1.250  Bcast:1.1.1.1  Mask:14.1.1.1
          inet6 addr: xxx0::xx:bxxf:fexxc:xxxx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7357802 errors:205 dropped:314 overruns:90 frame:0
          TX packets:8394562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:320913882 (306.0 MiB)  TX bytes:2647346096 (2.4 GiB)
          Interrupt:3

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:0.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19806473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19806473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:71695524 (68.3 MiB)  TX bytes:71695524 (68.3 MiB)
```

Look right after where it says "eth0". See that part that says "inet addr:192.168.1.250" ? 
192.168.1.250 is the computer's IP address.

---

### Post by a.v.l on 2007-09-19
> **qpieus said:**
> At the server computer, open up a terminal window and type

ifconfig

you'll get a response in the terminal window that looks something like this:

```
gdfgghh@server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 44:44:44:4C:54D:24
          inet addr:192.168.1.250  Bcast:1.1.1.1  Mask:14.1.1.1
          inet6 addr: xxx0::xx:bxxf:fexxc:xxxx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7357802 errors:205 dropped:314 overruns:90 frame:0
          TX packets:8394562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:320913882 (306.0 MiB)  TX bytes:2647346096 (2.4 GiB)
          Interrupt:3

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:0.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19806473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19806473 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:71695524 (68.3 MiB)  TX bytes:71695524 (68.3 MiB)
```

Look right after where it says "eth0". See that part that says "inet addr:192.168.1.250" ? 
192.168.1.250 is the computer's IP address.

Thanks for the advice. From your instructions above I've  been able to find my IP address and set up the clients PC as instructed. as an example.
 
ipp://192.168.2. 296/printers/Laserjet-1020

 I'm told the printer is ready on the client machine, but I'm unable to print a test page from this  computer.  The server PC  prints ok.  I'm lost now and have no where else to go other than to rely on you kind people for help.

---

### Post by qpieus on 2007-09-22
It sounds like the print server is not allowing the client pc to connect properly. The printer sharing function is controlled, in part, by a file called cupsd.conf in the /etc directory. Please open that file and copy the contents and paste it here. Then I can compare it to mine and maybe we'll see what's wrong. By the way, are you using dapper 6.06 as your profile says? I am too, but I use kubuntu rather than ubuntu, so I won't be able to give you gui directions very easily since the interface is different. That's ok though, we should be able to directly edit some config files to make any changes we need.

Also, when I set up my print server, I used a guide I found somewhere - I'll try to find that and give it to you for additional help. I remember when I set it up I had no idea what I was doing :) and the guide walked me through it no problem.

---

### Post by a.v.l on 2007-09-25
> **qpieus said:**
> It sounds like the print server is not allowing the client pc to connect properly. The printer sharing function is controlled, in part, by a file called cupsd.conf in the /etc directory. Please open that file and copy the contents and paste it here. Then I can compare it to mine and maybe we'll see what's wrong. By the way, are you using dapper 6.06 as your profile says? I am too, but I use kubuntu rather than ubuntu, so I won't be able to give you gui directions very easily since the interface is different. That's ok though, we should be able to directly edit some config files to make any changes we need.

Also, when I set up my print server, I used a guide I found somewhere - I'll try to find that and give it to you for additional help. I remember when I set it up I had no idea what I was doing :) and the guide walked me through it no problem.

*************************************

Thanks, this is the content of my  cupssd.conf file. My version of ubuntu is Edgy Elf 6.10


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

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

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
</Policy>

#
#

---

