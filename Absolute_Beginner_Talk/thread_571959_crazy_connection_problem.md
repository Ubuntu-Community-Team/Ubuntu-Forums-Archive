---
title: "crazy connection problem"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by scholzilla on 2007-10-09
Hi friends,

I'm having a strange problem with my home internet, but my provider swears it's not them. I can't connect at all from home either via wireless (linksys WTG-54) or via wired connection, but I can connect without problem via wifi at cafes etc. When at home, my provider can see my modem (strong signal) and can even ping my computer; my network manager software (wicd) also tells me that I am connected with the right IP address and all my modem lights are lit as they should be. Nonetheless, I can't access the internet (web through firefox, pinging, or using other apps). This seems really strange to me, especially b/c I had been connecting from home fine for about six months prior to this and, again, I can connect from elsewhere now. I don't know where to begin troubleshooting this and was hoping someone else might. 

Here are my goods. 

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:E0:B8:D3:D8:D5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth0:avah Link encap:Ethernet  HWaddr 00:E0:B8:D3:D8:D5  
          inet addr:169.254.12.83  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:212 (212.0 b)  TX bytes:212 (212.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:C0:A8:D8:96:A1  
          inet addr:192.168.0.217  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fed8:96a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3794373 (3.6 MiB)  TX bytes:811809 (792.7 KiB)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-D8-96-A1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.422 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"EPICCAFEYO"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:0F:B3:52:23:5D   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality=48/64  Signal level=33/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by HermanAB on 2007-10-09
OK, well, there is a lot more to it than just your IP address.  The file /etc/resolv.conf should show the name servers.  The routing table should have a default route pointing to your gateway.  To your computer, your home router is your gateway.  The home router should however have the ISP gateway programmed in it.

So, do some tests:
Do you have a default route?
$ sudo route
(this may take a while)

If not, add a default route:
$ sudo route add default gw your.gateway.ip.address dev wlan0

Do you have DNS configured?
$ cat /etc/resolv.conf

If not edit the file and add lines like:
nameserver dns.ip.addr.ess

Does your DNS work?
$ nslookup [www.yahoo.com](www.yahoo.com)

Is your DNS fast or lame?
$ dig @dns1.ip.add.ess [www.yahoo.com](www.yahoo.com) 
$ dig @dns2.ip.add.ess [www.yahoo.com](www.yahoo.com)
$ dig @dns3.ip.add.ess [www.yahoo.com](www.yahoo.com)

Put the fastest DNS at the top of the list in /etc/resolv.conf.

'Hope this helps!

Herman

---

### Post by scholzilla on 2007-10-09
Thanks a lot for the response. Here's what I gots:

The file /etc/resolv.conf should show the name servers. 

==> It does have name servers:

search domain.actdsltmp
nameserver 192.168.0.1
nameserver 205.171.3.65

Do you have a default route?
$ sudo route

=====>Yep. Here's what I get:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
default         *               0.0.0.0         U     1000   0        0 eth0


Do you have DNS configured?
$ cat /etc/resolv.conf

===>I get this:

search domain.actdsltmp
nameserver 192.168.0.1
nameserver 205.171.3.65

Does your DNS work?
$ nslookup [www.yahoo.com](www.yahoo.com)

=====> seems to:

Server:         205.171.3.65
Address:        205.171.3.65#53

Non-authoritative answer:
[www.yahoo.com](www.yahoo.com)   canonical name = [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net).
Name:   [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net)
Address: 209.191.93.52


Is your DNS fast or lame?
$ dig @dns1.ip.add.ess [www.yahoo.com](www.yahoo.com)
$ dig @dns2.ip.add.ess [www.yahoo.com](www.yahoo.com)
$ dig @dns3.ip.add.ess [www.yahoo.com](www.yahoo.com)

=====> I'm not sure what I'm doing here, but here's what I did:

dig @205.171.3.65 [www.yahoo.com](www.yahoo.com)

; <<>> DiG 9.3.4 <<>> @205.171.3.65 [www.yahoo.com](www.yahoo.com)
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 16813
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 8, ADDITIONAL: 8

;; QUESTION SECTION:
;[www.yahoo.com](www.yahoo.com).                 IN      A

;; ANSWER SECTION:
[www.yahoo.com](www.yahoo.com).          180     IN      CNAME   [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net).
[www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net). 45    IN      A       209.191.93.52

;; AUTHORITY SECTION:
akadns.net.             50910   IN      NS      asia9.akadns.net.
akadns.net.             50910   IN      NS      zc.akadns.org.
akadns.net.             50910   IN      NS      use3.akadns.net.
akadns.net.             50910   IN      NS      zd.akadns.org.
akadns.net.             50910   IN      NS      usw2.akadns.net.
akadns.net.             50910   IN      NS      eur1.akadns.net.
akadns.net.             50910   IN      NS      za.akadns.org.
akadns.net.             50910   IN      NS      zb.akadns.org.

;; ADDITIONAL SECTION:
usw2.akadns.net.        151270  IN      A       65.114.105.4
zc.akadns.org.          2926    IN      A       124.211.40.4
za.akadns.org.          3446    IN      A       195.219.3.169
asia9.akadns.net.       144010  IN      A       220.73.220.4
eur1.akadns.net.        144010  IN      A       213.254.204.197
zd.akadns.org.          2768    IN      A       63.209.3.132
use3.akadns.net.        151270  IN      A       204.2.178.133
zb.akadns.org.          280     IN      A       206.132.100.105

;; Query time: 49 msec
;; SERVER: 205.171.3.65#53(205.171.3.65)
;; WHEN: Tue Oct  9 20:17:29 2007



Put the fastest DNS at the top of the list in /etc/resolv.conf.

-----
Does this tell you anything??

Thanks again. I may take a day to get back to you as I can't connect from home.....

---

### Post by HermanAB on 2007-10-09
Well, that shows that most things are working and your DNS at 49ms is reasonable too.

IP Address: OK
Default route: OK
DNS: OK

Try these:
$ ping [www.yahoo.com](www.yahoo.com)

You should get a bunch of responses

$ telnet [www.yahoo.com](www.yahoo.com) 80

You should get a banner.  
(press ctrl-], q to quit)

If that works, then Firefox should work too.

Cheers,

H.

---

### Post by scholzilla on 2007-10-09
that all works fine....from the cafe. Again, though, at home I can't even connect despite my AP's being able to see me fine and my network manager software saying I'm connected.

thanks again,

m

---

### Post by HermanAB on 2007-10-10
Sure, but you have to run through those tests again.  If everything is right and it doesn't work, then something is wrong...
;)

---

### Post by kvonb on 2007-10-10
It could be a WEP/WAP/Encryption problem.

What make/model of wireless adapter are you using?

Maybe give us the output from the following:

lspci | grep net
lsusb (if it is a USB adapter)
ifconfig -a

I would also install the rather cool and useful "netapplet" util through Synaptic (when you are at the cafe obviously!), and run that (press alt-f2 and type: netapplet).

It allows you to switch between connections and also gives you some useful info.

---

