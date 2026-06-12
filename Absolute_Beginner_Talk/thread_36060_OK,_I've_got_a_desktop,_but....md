---
title: "OK, I've got a desktop, but..."
date: 2005-05-21
forum: Absolute Beginner Talk
---

### Post by tinker on 2005-05-21
OK, I've got a desktop, but that's about as far as I seem to be able to get (aside from setting some preferences and playing with text editors).

My immediate issues are seeing and being seen on my LAN, and getting online with my dialup external modem.

Whenever I try to run: 

System>Administration>Login Screen Setup
System>Administration>Networking
System>Administration>Shared folders
System>Administration>Time and Date
System>Administration>Users and Groups

I get a dialog box requesting a password.  Entering either user or root gives me another box:

Error
Failed to run...
Child terminated with 1 status

Now I'm a total noobie, but I don't want to terminate any children here...

I haven't even gotten to the modem yet.  Can anyone guide me?  Thanks.

The domestic scene intervenes...  I'll check back in later.

---

### Post by f.prisson on 2005-05-21
I come from debian and don't know Ubuntu that good, but I have read that the root account is disabled for security purposes and you have to issue your commands with sudo.

You can set the root password with ```
sudo passwd root
``` , set a new password and then enter it if the password dialog appears for administrative applications.Only work with it when needed!

---

### Post by ssam on 2005-05-21
those should take you user password. check you have not got capslock on or anything like that.

if you open a terminal and type
```
 sudo network-admin
``` 
then press enter, and enter your user password. does that work?

---

### Post by ssam on 2005-05-21
the root account is disabled by default, but the first user has sudo priviliges, and can run admin tasks. this user must type  his/her password each time they do this for security reasons.

in some ways this is more secure than having a root account.

you can enable the root account, but it is best not to unless you know what you are doing.

read

[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

---

### Post by tinker on 2005-05-21
I re-established root password.  
Tried to run: System>Administration>Networking
Entered root passwd>"Failed to run network-admin" "Wrong password"
Same with user passwd>"Failed to run network-admin" "Wrong password"

[Domesticity intervenes...  I'll check back later.]  Thanks.

---

### Post by tinker on 2005-05-21
[QUOTE=ssam]those should take you user password. check you have not got capslock on or anything like that.

if you open a terminal and type
```
 sudo network-admin
``` 
then press enter, and enter your user password. does that work?[/QUOTE]
 Yes, that worked, ssam.  It shows that my ethernet connection is active, but I still can't browse my network.

I'll check back in 4 or 5 hours... I've got to go fishing.

---

### Post by tinker on 2005-05-21
Alright, here's where I'm at now:

Network settings>Ethernet eth0 connection showing active.
However, the machine is not showing up in NetworkNeighborhood>EntireNetwork>Workgroup on the other two Win machines on the LAN.

When I run [# sudo network-admin] from terminal I get:
(network-admin:12722) : GnomeUI-WARNING **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Then the 'Network settings' frame appears showing eth0 is active.

'Properties'>'device configured' is checked.  Configuration set to DHCP. 'IP address', 'Subnet mask' and Gateway address are blank.  I have no clue what could or should be entered in these fields.

'General' tab shows Hostname, but Domain name is blank -- I have no idea what to enter here...
'DNS' tab shows 'DNS Servers' as blank. 
'Search Domains' shows [xxxxxx.xxx] -- the domain I entered with the machine name on Ubuntu install.
A number of cryptic IP addresses and Aliases appear under the 'Hosts' tab along with the name I gave in install, plus 'localhost.localdomain'.

When I 'OK' out of Network settings the terminal I used to get into it with [# sudo network-admin] shows:
** (network-admin:12722) : CRITICAL **: gst_xml_element_destroy: assertion 'node!= NULL' failed.

It's clear, I'm sure, that I know nothing about networking aside from Windows Wizards...
I need more help.  Thanks.

---

### Post by poofyhairguy on 2005-05-21
[QUOTE=tinker]  It shows that my ethernet connection is active, but I still can't browse my network.
.[/QUOTE]

You need samba for that:

ubuntuguide.org

---

### Post by kleeman on 2005-05-21
guis are distracting  :smile:  :smile: 
Open up a terminal window and type ifconfig and report
your output. This shows a lot of info on the status of your network connection

---

### Post by tinker on 2005-05-22
ifconfig:
Link encap:Ethernet  HWaddr 00:E0:29:86:2B:B3
inet6 addr: fe88::2e0:29ff:fe86:2bb3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
RX packets:1382 errors:0 dropped:0 overruns:0 frame:0
TX packets:559 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:419050 (409.2 Kib)   TX bytes:150351 (146.8 Kib)
Interrupt:9  Base address:0xf400

lo
Link encap:Local Loopback
inet  addr:127.0.0.1  Mask:255.0.0.0
inet6 addr:  ::1/128  Scope:Host
UP LOOPBACK RUNNING  MTU:16436   Metric:1
RX packets:222378 errors:0 dropped:0 overruns:0 frame:0
TX packets:222378 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:20258402 (19.3 Mib)   TX bytes:20258402 (19.3 Mib)

---

### Post by tinker on 2005-05-22
[QUOTE=poofyhairguy]You need samba for that:

ubuntuguide.org[/QUOTE]
 Thanks.

I ran [# apt-get install samba]...
After prompting to insert Ubuntu disk and a number of lines of text I got:
TDBSAM converted successfully.
 * Starting Samba daemons..

I assume it is now running, though still unable to browse or be browsed.

---

### Post by poofyhairguy on 2005-05-22
[QUOTE=tinker]
Then the 'Network settings' frame appears showing eth0 is active.[/QUOTE]

Quick note for you: that doesn't mean that its active (if you couldn't guess). Its one of the bigger bugs (all software has a few).

---

### Post by tinker on 2005-05-22
[QUOTE=poofyhairguy]Quick note for you: that doesn't mean that its active (if you couldn't guess). Its one of the bigger bugs (all software has a few).[/QUOTE]

I'm cool with that.  Terminal mode seems to be the way to go.  I'm hoping for some interpretation of my results from the 'ifconfig' command:

ifconfig:
Link encap:Ethernet HWaddr 00:E0:29:86:2B:B3
inet6 addr: fe88::2e0:29ff:fe86:2bb3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1382 errors:0 dropped:0 overruns:0 frame:0
TX packets:559 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:419050 (409.2 Kib) TX bytes:150351 (146.8 Kib)
Interrupt:9 Base address:0xf400

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:222378 errors:0 dropped:0 overruns:0 frame:0
TX packets:222378 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:20258402 (19.3 Mib) TX bytes:20258402 (19.3 Mib)

Thanks.  
Tinker (Greenest of Newbies)

---

### Post by kleeman on 2005-05-22
The first interface of your output I assume is eth0 (the second is lo) . It's not showing an IP address (eg something like 192.168.0.100) so that suggests it is up but your router has not given it an address - this explains why it isn't working  :smile: Try to prompt your router with:

sudo dhclient eth0

and report your output....

---

### Post by Ali_Baba on 2005-05-22
Im not sure but i have this kind of line in my ifconfig :
inet addr:"my ip"  Bcast:"broadcast address"  Mask:"mask adress" 
maybe you should get that line to your ifconfig.

---

### Post by tinker on 2005-05-22
[QUOTE=kleeman]The first interface of your output I assume is eth0 (the second is lo) . It's not showing an IP address (eg something like 192.168.0.100) so that suggests it is up but your router has not given it an address - this explains why it isn't working  :smile: Try to prompt your router with:

sudo dhclient eth0

and report your output....[/QUOTE]
 Apologies. I should have been more specific about my LAN. 
Running [# sudo dhclient eth0] proved I have "no working leases in my database" -- 'dhclient' is snoozing again...

This LAN is an in-home peer-to-peer (PPP?) that includes file & print sharing.  IP addresses are obtained automatically.  No DHCP server. No default Gateway. No DNS server. No WINS server.

The two other machines are Win98SE/XP, with a dial-up modem each (hence, my ability to conduct this exchange with the forum).

The WinXP machine uses Automatic Private Address yet shows:
IP Address: 169.254.xx.xxx
Subnet Mask: 255.255.0.0

It seems harder to fathom these numbers on the Win98SE, but they've been working together for years with no difficulty.

Thanks.

(Note to Ali_Baba: Sounds good, but I have no clue of how to go about adding those lines. Thanks.)

---

### Post by kleeman on 2005-05-22
Bit outside my experience I'm afraid. Here is a dial-up modem howto to try:

[http://www.ubuntulinux.org/wiki/DialupModemHowto](http://www.ubuntulinux.org/wiki/DialupModemHowto)

---

### Post by Ali_Baba on 2005-05-23
Try if you write that same kind of line like I said to ifconfig. Your ip-address and mask and broadcast address,like I have.Maybe that could help,dont know for sure.

---

