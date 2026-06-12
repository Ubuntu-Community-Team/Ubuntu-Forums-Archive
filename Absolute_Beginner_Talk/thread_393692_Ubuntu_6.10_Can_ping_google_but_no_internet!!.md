---
title: "Ubuntu 6.10 Can ping google but no internet!!"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2007-03-26
I am new to linux and have just installed ubuntu 6.10. The network card has been detected and it seems to be correctly configured (I have a DHCP router NetGear WGR614 v6).

I can ping [www.google.com](www.google.com), and also other computers in the network.

But - when I start Firefox and try to look up [www.google.com](www.google.com), it gives me a unable to connect error message.

What can I do to fix the problem?

Many thanks!!

Anders

---

### Post by NikoC on 2007-03-26
I don't use firefox at the moment and this might sound dumb, but did you uncheck the 'Work offline' option under 'File' menu?

---

### Post by cowlip on 2007-03-26
make sure there are no proxies selected as well, in Firefox options.

Can you access your router's configuration page in Firefox? ([http://192.168.*.*](http://192.168.*.*), AKA whatever your router's IP adress is)  Have you tried another browser like Epiphany, Opera, or Konqueror?

could try to disable ipv6: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by profXavier on 2007-03-26
Do you have any addons for Firefox?  Have you just started using Firefox, and if not, was it working properly before?

---

### Post by ahlandberg on 2007-03-26
Ubuntu is freshly installed. 

No modifications have been made to Firefox. 

It is definetely not in "Work Offline" mode.

I haven't had it installed before.

No add-ons or proxies installed as far as I can see.

I can access my router's login page: routerlogin.net.


Strange stuff - I don't understand. Please help!!

Anders

---

### Post by cowlip on 2007-03-26
can you access IP addresses of web sites from Firefox, or another browser?

Google's IP: 64.233.187.99

can you copy and paste (maybe to a file on your other networked computers) the outputs of ifconfig, iwconfig, and /etc/network/interfaces ?

---

### Post by ahlandberg on 2007-03-26
Ok, when I enter the IP 64.233.187.99 I can access Google, and I can search for sites and also access them. But again, when I type e.g. [www.php.net](www.php.net) directly, again unable to get a connection.

Will send you the ifconfig etc. dumps soon.

Anders

PS: What DNS address do I need?

My Router's IP is 192.168.1.2, but when I set it to that, it still doesn't work.

---

### Post by cowlip on 2007-03-26
Yes, it sounds like it's just a DNS problem.  Try some of the solutions here: [http://www.opendns.com/start/at_home.php](http://www.opendns.com/start/at_home.php) or [http://208.67.219.39/start/at_home.php](http://208.67.219.39/start/at_home.php)

Maybe someone in the networking forum can help you better [http://ubuntuforums.org/forumdisplay.php?f=136](http://ubuntuforums.org/forumdisplay.php?f=136)

---

### Post by freebird54 on 2007-03-26
You MIGHT be experiencing a problem with ipv6 confusing your router.  First thing to try, if so, is to type **about:config** into Firefox's address bar.  Search for **ipv6**.  The **network.dns.disableipv6** option should be double-clicked to select (turns bold).

If this helps - then I can post instructions for permanently disabling it on a system-wide basis....

---

### Post by ahlandberg on 2007-03-26
I had a look at the links but just couldn't figure it out. 

Anyway, here is the info:



ahlandberg@ubuntu610:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:1B:30:CB  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe1b:30cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:504623 (492.7 KiB)  TX bytes:154240 (150.6 KiB)
          Interrupt:177 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)




ahlandberg@ubuntu610:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.




/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.1.2

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




My Router's IP is 192.168.1.2, and I have a DSL modem which is on 192.168.1.1. The Router hangs on the modem, and the LAN is connected to the router.

---

### Post by ahlandberg on 2007-03-26
I went to about:config in Firefox and double-clicked network.dns.disableipv6, so now it is set to trye (bold).

But still, same problem.

Entering the IP addresses and pinging works, but no URLs.

Please help!!

Anders

---

### Post by ahlandberg on 2007-03-26
Hello,

I changed my DNS server to the address of the modem (192.168.1.1) and it works now!

Thanks all for your help!

Anders

---

