---
title: "Can't connect to Internet, but can share files on network"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by vishagan on 2007-05-14
Hi all. I'm using a Ubuntu/XP dual boot on my machine. I connect to the internet through my college dorm's network which uses DHCP I believe. On my XP, internet works fine. On Ubuntu however, I only have file sharing capabilities with the rest of my peers on my network. I do not have internet. I can access M*cr*s*ft Networks on LAN but not internet on Firefox. On XP, we were instructed by the college to use proxy:

                        **Proxy: apartment02       Port: 80**

And this is the Network Connection Details for my successful XP network

[B]Physical Address: 00-13-46-3A-F6-8D

IP Address: 172.20.69.59

Subnet Mask: 255.255.255.0

Default Gateway: 172.20.69.1

DHCP Server: 172.18.64.223

Lease Obtained: 5/15/2007 12:16:48 AM

Lease Expires: 5/18/2007 12:16:48 AM

DNS Server: 172.18.64.223

WINS Server: 172.18.64.223[/B]

How do i get internet to work on my ubuntu? I've set eth0 connection to use DHCP...and thats how i got file sharing to work. Any other settings like IPv4 or Static IP doesnt work. And I've also set the proxy in Firefox. How do i make it work?

Thank you in advance.

---

### Post by blazercist on 2007-05-14
what is the output of command sudo ifconfig in console?

---

### Post by lazyart on 2007-05-14
What is the network info from ubuntu?

---

### Post by lamalex on 2007-05-14
triple check your proxy settings, you probably have something wrong there

---

### Post by vishagan on 2007-05-14
This is what ifconfig gave me. And i rechecked my proxy... its correct.

**eth0 **     

[B]Link encap:Ethernet  HWaddr 00:13:46:3A:F6:8D            
inet addr:172.20.69.59  Bcast:172.20.69.255  Mask:255.255.255.0          
inet6 addr: fe80::213:46ff:fe3a:f68d/64 Scope:Link          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          
RX packets:72 errors:0 dropped:0 overruns:0 frame:0          
TX packets:70 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:1000           
RX bytes:7609 (7.4 KiB)  TX bytes:7184 (7.0 KiB)          
Interrupt:21 Base address:0x6000[/B]

**lo **
[B]
Link encap:Local Loopback            
inet addr:127.0.0.1  Mask:255.0.0.0          
inet6 addr: ::1/128 Scope:Host          
UP LOOPBACK RUNNING  MTU:16436  Metric:1          
RX packets:2 errors:0 dropped:0 overruns:0 frame:0          
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:0          
RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
[/B]

---

### Post by blazercist on 2007-05-14
have you tried to ping an external address? it may be a dns problem...

try "ping 64.233.167.99" in console.

---

### Post by lazyart on 2007-05-14
....and ping the proxy server

---

### Post by vishagan on 2007-05-14
I managed to ping the proxy server with 97% sent... and the 64.233.167.99 ping in XP says "Request Time Out". I haven't tested the 64.233.167.99 ping on Ubuntu anyway. Could it be some protocol problem? I can't use the Add/Remove application either.

---

### Post by blazercist on 2007-05-16
Thats very odd, the ip i gave you to ping was google, it should come up, if you can ping the proxy then its a proxy issue.

---

### Post by vishagan on 2007-05-16
blazercist: i don't quite get you. Are you saying that the problem is with my proxy? And why cant i ping Google from my XP installation? Is it possible that the proxy server is configured for Windows only? I mean, can they do that? And can they block ping attempts to external servers? Sorry for so many questions but it really bugs me that i cant use internet on Ubuntu as its quite useless for me without Internet.

---

### Post by blazercist on 2007-05-17
Hmm, it is possible that they are blocking ping attempts, it is even possible to block internet access by OS, but I don't understand why a college proxy would do such a thing especially with so many people using linux and mac.  If you CAN NOT ping google from your XP machine but you CAN see google.com in your browser it means that the ping requests are being blocked.

Whats more interesting is that your windows install has internet and file sharing while your Linux only has file sharing, this means that you have gotten a network ip from your college's router or whatever switch they are using for networking,  but the router/switch is not letting you out of the LAN, this is most likely due to incorrect proxy settings.

Are there any applications that you use in windows that use the internet and do not have to be configured to work through the proxy?  For example, do you use AIM and its not configured to work through the proxy?   Is only web browsing restricted through the proxy?  If so then you can try to use GAIM from linux and see if it connects.  If it does then you know for sure that you've misconfigured the proxy settings on your browser.  Other than that I don't know.

If you think its because of your OS, you could always try to install internet explorer using wine and see if that works, but you would have to download all the stuff from your XP partition and move it over.

EDIT:  You know what, I've thought about it and I realized that if you were pinging google from cmd prompt in windows and your college only has an http proxy then it would bounce off.  Try putting that ip in firefox like this http://<ip goes here> and see if it works.

---

### Post by vishagan on 2007-05-19
Actually, I'm living in Malaysia. And it's very hard to come by students who use or even know how to use Linux or Mac here in my college. 99.5% of computers here use Windows. Maybe the college generalized that no one uses Linux or Mac. I'll check with the college administration anyway. My college is quite weird when it comes to networking.

I tried **[http://64.233.167.99/](http://64.233.167.99/)** on Windows Firefox and Internet Explorer. Both gave me an error message like this:

  [B]  *  Error Code 64: Host not available
    * Background: The gateway or proxy server lost connection to the Web server.
    * Date: 5/19/2007 9:54:52 AM
    * Server: APARTMENT02
    * Source: Remote server [/B]

Btw, the only softwares I use that don't require proxy configuration are iTunes and MSN Messenger. I use them with no problems at all on Windows. I haven't tried GAIM on Ubuntu however. I'll try it soon and update you with the results. I've gotta reboot my computer to switch to Ubuntu now.

Just for your information,I did run into some problems installing Ubuntu. Had to install it from the Live CD as the Alternate CD won't. That same Alternate CD worked fine on other machines. It had something to do with the "/sbin/modprobe" exiting abnormally as it couldn't find the necessary files (as far as I could understand the problem). Could this be related to that? My hardware?

---

### Post by my_key on 2007-05-19
Are you shure it isn't just a DNS problem? Most of the time when i get a "i can connect with windows, but not with linux"-question i just have to type the dns servers in their network settings. Try to do a tracepath to [www.google.com](www.google.com) and see if it can resolve the ip. If it can't, just fill in the dns servers in your network properties or edit your resolv.conf (find them by googling for your isp's name and dns servers).

---

### Post by vishagan on 2007-06-01
Finally solved the issue... I entered the proxy server in IP address terms i.e. 172.18.64.222 instead of apartment02 and it worked. Never knew it was that easy. Sorry if this has wasted ur time guys... i never knew it could be solved like this. Thanx for the help anyway. ;)

---

