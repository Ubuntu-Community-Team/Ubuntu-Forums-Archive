---
title: "[SOLVED] Help! lost wired connection!"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Helios1276 on 2008-03-29
Im still green when it comes to Ubuntu and as I was installing stuff last night I somehow lost my wired connection!

---

### Post by DBrocks on 2008-03-29
Have you tried pinging google.com?

```
ping -c 2 google.com
```

---

### Post by DBrocks on 2008-03-29
And, are you using DHCP for an IP address, or have you set your own static IP?

---

### Post by DBrocks on 2008-03-29
You should be able to run
```
sudo dhclient eth0
```

then

```
sudo /etc/init.d/networking restart
```

That may do it.

---

### Post by Helios1276 on 2008-03-29
Ok, im using dchp(wired to router). I pinged google.com and got '2 packets transmitted, 0 received, 100% packet loss'. I also tried those comands you gave me which ended in * Reconfiguring network interfaces...but when i tried my browser I still cant get anything

---

### Post by DBrocks on 2008-03-29
Can you post the contents of
```

ifconfig
```

---

### Post by DBrocks on 2008-03-29
And do you know you router's IP address?

---

### Post by Joeb454 on 2008-03-29
DBrocks, please stop posting so much!! You can ask more than 1 thing in 1 post.

Also if you have an after-thought you can edit the post (it's where the thanks feature is :))

---

### Post by DBrocks on 2008-03-29
> **Joeb454 said:**
> DBrocks, please stop posting so much!! You can ask more than 1 thing in 1 post.

Also if you have an after-thought you can edit the post (it's where the thanks feature is :))

Yes I know. Lol sorry. I'll try and remember that. :lolflag:

---

### Post by Joeb454 on 2008-03-29
No worries :) It can get a bit confusing to read that's all ;)

---

### Post by DBrocks on 2008-03-29
> **Joeb454 said:**
> No worries :) It can get a bit confusing to read that's all ;)

Okay. So, what do you think his problem is?
I think maybe his gateway setup for his router got reset.
Maybe a hardware problem: unlikely

---

### Post by Helios1276 on 2008-03-29
Sorry about the delay, had to find the flash drive to move it over.

eth0      Link encap:Ethernet  HWaddr 00:16:36:38:DE:07  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe38:de07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21474 (20.9 KB)  TX bytes:18125 (17.7 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1456 (1.4 KB)  TX bytes:1456 (1.4 KB)

---

### Post by DBrocks on 2008-03-29
You probably need to reset your router gateway.
Try 
```
sudo route add default gw ROUTERIPADDRESS
```
And if that works, we can make it permanent.

---

### Post by Helios1276 on 2008-03-29
I got = ROUTERIPADDRESS: unknown host

---

### Post by DBrocks on 2008-03-29
No, you don't type in "ROUTERIPADDRESS" you substitute "ROUTERIPADDRESS" for the IP of the router. If a linksys: default is 192.168.1.1. Sorry if I wasn't clear enough.:lolflag:

---

### Post by Helios1276 on 2008-03-29
lol no worries , your dealing with monkey see monkey do here!
ok, I got= SIOCADDRT: File exists

---

### Post by DBrocks on 2008-03-29
Okay now try
```
sudo /etc/init.d/networking restart
```

then ping your router:
```
ping -c 2 THEIPOFYOURROUTER.
```

If the above is successful, ping google. If it's not, come back and tell me.

```
ping -c 2 google.com
```

---

### Post by Helios1276 on 2008-03-29
Ok, the story so far is 

shane@Acer:~$ sudo route add default gw ROUTERIPADDRESS
[sudo] password for shane:
ROUTERIPADDRESS: Unknown host
shane@Acer:~$ sudo route add default gw 192.168.2.1
SIOCADDRT: File exists
shane@Acer:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
shane@Acer:~$ ping -c 2 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=0.349 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=0.376 ms

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 0.349/0.362/0.376/0.023 ms
shane@Acer:~$ ping -c google.com
ping: bad number of packets to transmit.
shane@Acer:~$ ping -c 2 google.com
PING google.com (64.233.167.99) 56(84) bytes of data.
From Acer.local (192.168.2.5) icmp_seq=1 Destination Port Unreachable
From Acer.local (192.168.2.5) icmp_seq=2 Destination Port Unreachable

--- google.com ping statistics ---
2 packets transmitted, 0 received, +2 errors, 100% packet loss, time 1001ms

---

### Post by DBrocks on 2008-03-29
Could you post the contents of 
```
/etc/network/interfaces
```

---

### Post by Nythain on 2008-03-29
at this point im gonna have to say this is really sounding like a router configuration problem... he's getting connection to the router, just not beyond, possibly enabled teh firewall, or some form of port blocking/security??? everything else appears to be set up correctly and working correctly now...

possibly try resetting the router itself to factory defaults???

---

### Post by Helios1276 on 2008-03-29
for that last command i get 'permission denied' or when i add sudo I get command not found?? Theres an xp machine on the router at the moment(one i'm using), it generally works fine barring the odd loss of connection that has the same systems as this but it has never happened to any of the xp machines while they were wired.

---

### Post by DBrocks on 2008-03-29
no post the contents of the file "/etc/network/interfaces" :lolflag:

Also try
```
sudo iptables -F
```then
```
sudo /etc/initd./networking restart
```

and ping google

---

### Post by Helios1276 on 2008-03-29
Ok, I can't find that file....:frown: and when I try the ast command I get= iptables v1.3.6: no command specified Try iptables -h or iptables --help for more information.

---

### Post by DBrocks on 2008-03-29
```
sudo nano /etc/network/interfaces
```

Will give you the file.

---

### Post by Helios1276 on 2008-03-29
WAIT..WAIT! it worked!! :popcorn: . Thanks a million man! You have an unnending amount of patience:lolflag:

---

### Post by DBrocks on 2008-03-29
Wait, before you get too happy, make sure you can reboot, and still connect

---

### Post by Helios1276 on 2008-03-29
ya...rebooted ..unable to connect

---

### Post by DBrocks on 2008-03-29
try
```
sudo dhclient eth0
```
followed by:
```
sudo /etc/init.d/networking restart
```

---

### Post by Helios1276 on 2008-03-29
ok

shane@Acer:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:36:38:de:07
Sending on   LPF/eth0/00:16:36:38:de:07
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.5 -- renewal in 940676562 seconds.
shane@Acer:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
shane@Acer:~$

---

### Post by DBrocks on 2008-03-29
Now try using firefox to go to google. this time, DONT PING. It's not that you did anything wrong earlier, I've just seen some strange mis-leading things with ping.

---

### Post by Helios1276 on 2008-03-29
'Firefox can't establish a connection to the server at..'

---

### Post by DBrocks on 2008-03-29
please post the text that appears when you type:
sudo nano /etc/network/interfaces

---

### Post by Helios1276 on 2008-03-29
GNU nano 2.0.6         File: /etc/network/interfaces   

auto lo
iface lo inet loopback


















                                [ Read 6 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by DBrocks on 2008-03-29
Aahh well there's your problem! Here's what you need to do.
```

sudo nano /network/interfaces
```
This will open the network config file.

now add the following lines to the bottom of the file:
```

auto eth0 
iface eth0 inet dhcp
```

then

```
ctrl+o
```
(hold ctrl, and press "o") to save

```
ctrl+x
```
(hold ctrl, press "x") to exit

then
```
sudo /etc/init.d/networking restart
```

try to get to google with firefox

---

### Post by bumanie on 2008-03-29
Hi, Helios1276, DBrocks had been doing a stirling job trying to help. I don't want to butt in and upset anyone, however as nothing so far has worked could you try this. It may not work but it was the thing I mentioned the first time I had contact with you prior to you actually installing ubuntu. If I remember correctly, you were initially trying a wireless connection.
Anyway try this,
> sudo gedit /etc/modprobe.d/blacklist
At the bottom of the gedit list type balcklist ipv6 save and close.
Then open firefox and type in the address bar about:config
In the filter type ipv6, right click on the line of text that appears and left click on toggle to change the value to true. Log out and back in and see if firefox works.
If this doesn't work you can reverse the changes by removing the line that was added to the blacklist and toggle ipv6 back to false.

---

### Post by Helios1276 on 2008-03-29
GNU nano 2.0.6         File: /etc/network/interfaces                          

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp















                                [ Read 7 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

Ok, I ended up with that above , then saved and exited. Firefox wont connect still for some reason

---

### Post by DBrocks on 2008-03-29
did you restart the network?
```

sudo /etc/init.d/networking restart
```

also try bumanie's idea

---

### Post by DBrocks on 2008-03-29
*Bump* How's it going?

---

### Post by Helios1276 on 2008-03-29
hey bumanie, I gave that a go to no avail and I tried restarting the network too @Dbrocks. Im lost and frustrated lol

---

### Post by DBrocks on 2008-03-29
okay. We're going to give you a static IP now. We will see if that works any better.
1. Open the file
```
sudo gedit /etc/network/interfaces
```

remove the "auto eth0" and "iface eth0 inet dhcp" lines.

Now, add these following lines to the bottom of this file:

auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway YOURROUTER'SIPADDRESS

save and close
restart network```

sudo /etc/init.d/networkng restart
```
try to get to google from firefox.
Reboot your computer.
Try to get to google again.

---

### Post by Helios1276 on 2008-03-29
should I use 192.168.2 ...etc? i thought you might be thinking linksys ? im using a Belkin

---

### Post by DBrocks on 2008-03-29
Ah yes. Sorry. Yes use 192.168.2.XXX as your address. 192.168.2.0 for your network. 192.168.2.255 for broadcast. Leave the netmask the same. Sorry bout that.

Really though, the most important is the gateway though. But good job catching that: It could cause problems later, if you start a home network

---

### Post by Helios1276 on 2008-03-29
no , still no joy , made the changes and then tried again changing my ip a little .

---

### Post by DBrocks on 2008-03-29
Did you restart the network and your computer?

---

### Post by Helios1276 on 2008-03-29
it dosnt matter what my ip add end in right? like .100 or .17 or .9? . well i restarted the network and rebooted and still nothing. weird though, you had it running before?? wish I could help more

---

### Post by DBrocks on 2008-03-29
No, its okay thats why I'm here. Try 
```
sudo ifup eth0
```
```
sudo ifdown eth0
```

Restart network, restart firefox.

---

### Post by Helios1276 on 2008-03-29
ifdown: interface eth0 not configured(found something?)

---

### Post by DBrocks on 2008-03-29
Does Firefox work after doing Ifup and ifdown? Also, run ifup again.

---

### Post by Helios1276 on 2008-03-29
no Firefox still isnt working. ifup: interface eth0 already configured. gives me nothing new for ifdown( i'm restarting the network each time before trying firefox )

---

### Post by Helios1276 on 2008-03-29
bump:(

---

### Post by bumanie on 2008-03-29
Are you sure your ethernet port is functioning? Does it have the led lights on etc. May be the updates you did have knocked out the ethernet drivers. Sort of clutching at straws, but it would be terrible to go through all this and find the card isn't working. Double check all wired connections and if it's a pci card, check that it is seated properly.

---

### Post by Helios1276 on 2008-03-29
The leds seem fine (both lighting, though obviously the orange 'working' light fires rarely). I lost my connection last night around the time I was trying awn(which I coudnt get going) and screenlets( which are horrible and I got rid of ). Would posting a system log of some sort be a good idea for anyone trying to help?

---

### Post by DBrocks on 2008-03-29
Sorry, my mom forced me off the computer, made me do homework :popcorn:
Anyway: try pinging: 72.14.207.99. That's google's IP right now. You may have a problem with your DNS server.

Also, log onto your router: Try turning the firewall off.
Is there a button to reset the router to factor defaults? Try resetting it

---

### Post by Helios1276 on 2008-03-29
no worries man, though I'm glad your back! it said destination port unreachable?

---

### Post by DBrocks on 2008-03-29
Log into your router, and see if there's a way to turn off the firewall.
Also, try resetting the router to factory defaults.

---

### Post by DBrocks on 2008-03-29
> **bumanie said:**
> Are you sure your ethernet port is functioning? Does it have the led lights on etc. May be the updates you did have knocked out the ethernet drivers. Sort of clutching at straws, but it would be terrible to go through all this and find the card isn't working. Double check all wired connections and if it's a pci card, check that it is seated properly.

Drivers wouldn't be the problem: he was able to ping his router with no problem.

---

### Post by Helios1276 on 2008-03-29
restored factory setting and tried placing the linux machine's ip outside of the firewall , still nothing . Is there anyu equivalent of 'roll back' I could use to return to my pre-no conection settings?

---

### Post by DBrocks on 2008-03-29
Not really. However, I want to give this one more shot:
sudo gedit /etc/network/interfaces
remove all previous entries under eth0, but NOT LO
so, now you /etc/network/interfaces should have nothing in it concerning eth0. Now add in: 
```
iface eth0 inet dhcp
gateway: THE IP OF YOUR ROUTER
auto eth0
```Your /etc/network/interface should now look like: 
```
auto lo 
iface lo inet loopback 

iface eth0 inet dhcp
gateway: THE IP OF YOUR ROUTER
auto eth0
```Try restarting the network.



If that didnt work, try this:
```
 sudo ifdown eth0 --force
```
```
 sudo dhclient eth0
```

---

### Post by Helios1276 on 2008-03-29
still nothing, what the hell have i done to get screw this up!? lol would checking if the comp can get online through the modem without the router mean anything? i dunno, im wireless to the router now on a seperate xp machine

---

### Post by DBrocks on 2008-03-29
Yes, hook it up to the modem without the router, and run the commands I listed above one more time.

---

### Post by Helios1276 on 2008-03-29
still nothing so i guess the router is off the hook anyway. If i'm looking at a reinstall i'll cry cos getting the ati card running was tedious at best lol

---

### Post by DBrocks on 2008-03-29
Hook your computer back up to the router.

Now, try this:
1. Save your IPtables rules
```
 sudo iptables-save > /root/firewall.rules 
```

now use
```
sudo su
```to login as root
Enter the following commands.
```

iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
```Now, don't restart the network, just go straight to firefox.

---

### Post by Helios1276 on 2008-03-29
getting permission denied when I try the first command

---

### Post by DBrocks on 2008-03-29
try using ```
sudo su
``` first to login as root. Then try again

---

### Post by Helios1276 on 2008-03-29
right im just gonna show ya what happening so far, maybe your eyes seeing it wil help more 
cos im hitting constant road blocks due to a total lack of technical know how lol

shane@Acer:~$ sudo ifup eth0
[sudo] password for shane:
ifup: interface eth0 already configured
shane@Acer:~$ sudo ifdown eth0
shane@Acer:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
shane@Acer:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
shane@Acer:~$ sudo ifup eth0
ifup: interface eth0 already configured
shane@Acer:~$ sudo ifdown eth0
shane@Acer:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
shane@Acer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:38:DE:07  
          inet addr:192.168.2.17  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe38:de07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:513028 (501.0 KB)  TX bytes:90981 (88.8 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2288 (2.2 KB)  TX bytes:2288 (2.2 KB)

shane@Acer:~$ sudo /etc/init.d/networking restart
[sudo] password for shane:
 * Reconfiguring network interfaces...                                   [ OK ] 
shane@Acer:~$ ping -c 2 72.14.207.99
PING 72.14.207.99 (72.14.207.99) 56(84) bytes of data.
From 192.168.2.100 icmp_seq=1 Destination Port Unreachable
From 192.168.2.100 icmp_seq=2 Destination Port Unreachable

--- 72.14.207.99 ping statistics ---
2 packets transmitted, 0 received, +2 errors, 100% packet loss, time 999ms

shane@Acer:~$ sudo gedit /etc/network/interfaces
[sudo] password for shane:
shane@Acer:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:36:38:de:07
Sending on   LPF/eth0/00:16:36:38:de:07
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:36:38:de:07
Sending on   LPF/eth0/00:16:36:38:de:07
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.5 -- renewal in 940663103 seconds.
                                                                         [ OK ]
shane@Acer:~$ sudo ifdown eth0 --force
There is already a pid file /var/run/dhclient.eth0.pid with pid 6816
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:36:38:de:07
Sending on   LPF/eth0/00:16:36:38:de:07
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
shane@Acer:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:36:38:de:07
Sending on   LPF/eth0/00:16:36:38:de:07
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.5 -- renewal in 940663013 seconds.
shane@Acer:~$ sudo getdit /etc/network/interfaces
sudo: getdit: command not found
shane@Acer:~$ sudo gedit /etc/network/interfaces
shane@Acer:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:36:38:de:07
Sending on   LPF/eth0/00:16:36:38:de:07
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 10.92.128.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.92.128.1
bound to 89.100.249.13 -- renewal in 1450 seconds.
                                                                         [ OK ]
shane@Acer:~$ sudo ifdown eth0 --force
There is already a pid file /var/run/dhclient.eth0.pid with pid 7095
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:36:38:de:07
Sending on   LPF/eth0/00:16:36:38:de:07
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 89.100.250.1 port 67
shane@Acer:~$  sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 6925
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:36:38:de:07
Sending on   LPF/eth0/00:16:36:38:de:07
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.92.128.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 10.92.128.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.92.128.1
bound to 89.100.249.13 -- renewal in 1548 seconds.
shane@Acer:~$ sudo iptables-save > /root/firewall.rules
bash: /root/firewall.rules: Permission denied
shane@Acer:~$ sudo su
[sudo] password for shane:
root@Acer:/home/shane#  sudo iptables-save > /root/firewall.rules
root@Acer:/home/shane# iptables -x
iptables v1.3.6: no command specified
Try `iptables -h' or 'iptables --help' for more information.
root@Acer:/home/shane# sudo iptables -x
iptables v1.3.6: no command specified
Try `iptables -h' or 'iptables --help' for more information.
root@Acer:/home/shane#  sudo iptables-save > /root/firewall.rules
root@Acer:/home/shane#

---

### Post by DBrocks on 2008-03-29
okay, remember that Ubuntu is case-sensitive. Make sure it's a capital X, not a lower-case one. That could make all the difference

---

### Post by Helios1276 on 2008-03-29
was making my way through the commands there until i got to the -p INPUT ACCEPT part, at this point im getting 'unknown protocol 'input' specified

---

### Post by DBrocks on 2008-03-29
hmmm. try skipping it, and go on to the rest.

---

### Post by Helios1276 on 2008-03-29
Kepp getting the same response for the last three commands, tried Firefox anyway , it hangs at the 'connecting to google.com' part as opposed to unable to connect..'

---

### Post by DBrocks on 2008-03-29
Try these commands:

```
sudo /etc/init.d/iptables save
sudo /etc/init.d/iptables stop
```

---

### Post by Helios1276 on 2008-03-29
Just keeps saying 'command not found', I think I might need a drink now and try and bump this tomorrow maybe, if i fail after tomorrow then its a fresh install or back to m$:( Thanks for all your help man, its greatly appreciated here!

---

### Post by DBrocks on 2008-03-29
Yea, hang in there for a few more days.

---

### Post by lswest on 2008-03-29
can you post the output of these 2 commands:```
lshw -C network
sudo ifup eth0 && sudo ifdown eth0 && sudo dhclient eth0
```? (remember to keep the C capitalized in the first command, and the second line can just be entered as is, though it runs 3 commands at once) - I'll be awake for a while longer (though it is already 10:30 pm in Germany) and i'll keep thinking about this, and i'll bookmark this thread and check back tomorrow.

---

### Post by DBrocks on 2008-03-29
Do you by any chance have firestarter installed? that could be the source of your problems. Also, could you post the output of 
```
iptables -L
```

---

### Post by Helios1276 on 2008-03-31
Ok, back again for round 2!


shane@Acer:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: NetLink BCM5789 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 21
       serial: 00:16:36:38:de:07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5789-v3.49a ip=192.168.2.5 latency=0 module=tg3 multicast=yes
shane@Acer:~$ sudo ifup eth0 && ifdown eth0 && sudo dhclient eth0
[sudo] password for shane:
ifup: interface eth0 already configured
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
shane@Acer:~$ iptables -L
iptables v1.3.6: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
shane@Acer:~$ sudo su
root@Acer:/home/shane# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
moblock_in  0    --  anywhere             anywhere            state NEW MARK match !0x14 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
DROP       0    --  anywhere             anywhere            MARK match 0xa 
moblock_fw  0    --  anywhere             anywhere            state NEW MARK match !0x14 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
REJECT     0    --  anywhere             anywhere            MARK match 0xa reject-with icmp-port-unreachable 
moblock_out  0    --  anywhere             anywhere            state NEW MARK match !0x14 

Chain moblock_fw (1 references)
target     prot opt source               destination         
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain moblock_in (1 references)
target     prot opt source               destination         
RETURN     0    --  anywhere             anywhere            
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0

Chain moblock_out (1 references)
target     prot opt source               destination         
RETURN     0    --  anywhere             anywhere            
NFQUEUE    0    --  anywhere             anywhere            NFQUEUE num 0
root@Acer:/home/shane#

---

### Post by Helios1276 on 2008-03-31
BUMP *fingers crossed*

---

### Post by lswest on 2008-03-31
oh, crap, just realized my command was the wrong way around, should have been: ```
sudo ifdown eth0 && sudo ifup eth0 && sudo dhclient eth0
``` However, i don't think it will work, worth a try, but i doubt it.  Apart from that, i'm in over my head...

---

### Post by Helios1276 on 2008-03-31
If your in over your head that must make me screwed! lol..:(

---

### Post by lswest on 2008-03-31
Nah, don't worry, I'm just not much of a networking guy :P  Well, wired issues :S  Mainly cuz i never had issues with mine.  However, i do remember that once my ethernet did not work, since i had it disconnected during an install of a system and it wasn't configured during that time, and i had no GUI, didn't know the commands, etc. etc. and i just re-installed with the cable plugged in, configured the device, and (strangely, probably no link) the GUI worked too xD  So yeah...if you can stand to lose the data (or, better yet, if you have it split /home and /) you might try re-installing.  After all, you said it was working before.  But give it a bit of time, this post should bump the thread back up, maybe someone will come up with something? :P

---

### Post by Helios1276 on 2008-03-31
Ok, one last bump to try and avoid a reinstall

---

### Post by gtaskeraus on 2008-05-23
I noticed that you had moblock rules in your firewall.  Can you stop moblock and see if that will help you browse.

It caused me problems and a look at the system log files put me up to it.

---

### Post by jre on 2008-05-23
> **gtaskeraus said:**
> I noticed that you had moblock rules in your firewall.  Can you stop moblock and see if that will help you browse.

It caused me problems and a look at the system log files put me up to it.

I jumped a bit late in this thread and won't read everything ;-)
But I'm quite sure that you need to reconfigure MoBlock: You need to whitelist your LAN. 

If you don't know your local IP check it with "sudo ifconfig". It's the value after  "inet addr:" of the interface that you use for networking. For wired connections that might be "eth0", for wireless connections "wlan0".
 .
Example: You found out that your IP is 192.168.0.39. Then your LAN will most probably cover the IP range 192.168.0.1-192.168.0.255. Then set this in /etc/default/moblock and do a "moblock-control restart":
```
WHITE_IP_IN="192.168.0.0/24"
WHITE_IP_OUT="192.168.0.0/24"
```

jre

---

