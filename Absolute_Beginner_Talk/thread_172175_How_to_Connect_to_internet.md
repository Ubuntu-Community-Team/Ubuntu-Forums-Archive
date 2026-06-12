---
title: "How to Connect to internet"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by edmonds on 2006-05-08
There seem to  be many posts on  this but none actually explain how to - that i understand.

I have a router and a modem. This computer connects fine with win98, and other linux distros have connecte ok when installed on  this pc.

I  have looked at the internet /network box in  ubuntu and looked at the help file. But how do you get the connection working?

the router is dhcp, the ubuntu network iternet thing  has the dsl modem on dhcp.

sorry for being  dum

---

### Post by K2712 on 2006-05-08
What version of Ubuntu are you running?

Are you trying to connect via ethernet or wireless?

What is your ifconfig output?

---

### Post by edmonds on 2006-05-08
hi
sorry for the delay

eth0      Link encap:Ethernet  HWaddr 00:50:BF:98:55:63
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fe98:5563/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10510 (10.2 KiB)  TX bytes:1743 (1.7 KiB)
          Interrupt:11 Base address:0xd000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14628 (14.2 KiB)  TX bytes:14628 (14.2 KiB)


thanks
tom

---

### Post by K2712 on 2006-05-08
Have you checked this thread yet?

[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

If you still can't get it working, in order to help you I am going to need some more info:

What router are you using?
What are your computer specs?  (processor, NIC, Ubuntu version....)

---

### Post by edmonds on 2006-05-10
i followed the instructions - the network card is fine.
i  can ping [www.google.co.uk](www.google.co.uk).
i  can open a browser and go t google and do  a search.

But
I  can't click on  a google search  result.
i  can't go to ebay.co.uk or microsoft.com  or any other website.

My pc cannot connect to the ubuntu clock on  start up.

Its as if i can only connect to google, nothing  else.

any ideas?

---

### Post by K2712 on 2006-05-10
That is strange that you can ping google and search but can't get another site, sounds like it might be a browser issue.  Which browser and which version of java are you using?  Can you ping another site like yahoo?

Also post the contents of your /etc/network/interfaces file.

---

### Post by edmonds on 2006-05-12
its behaving  very oddly.
i  can ping google and yahoo, not microsoft or msn.
i can visit google and one of  my sites but not yahoo or msn.
it seems very random and different from 2 days ago.

Its firefox 1.0.8.

Not that i  can update anything  as i can't connect to any ubuntu server.

i did see the interface file - it doesn't say much (sorry i though i had saved it somewhere i could get it but i didn't - another 24hour delay)

---

### Post by Kobalt on 2006-05-12
Have you tried configuring your network access with 
```
sudo pppoeconf
```

---

### Post by mips on 2006-05-12
Ignore the above post as your network is kinda working. Issue is IPv6 or DNS related.

1. Disable IPv6:

```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak

sudo depmod -a
```

If the above did not do the job then proceed to step 2 below.

2. Manualyy configure your ISPs DNS servers by editing your **/etc/resolv.conf** file. Remove the entry for your routers address and add your ISP's 2 DNS server IP addresses. You will have to get the dns server ips from your isp.

---

### Post by edmonds on 2006-05-12
yes!
phoned up isp, homecall, got 2 dns addresses and added them in  the System>Administration>Networking>EthernetConnection>DNS Tab>Add

magic, thanks

---

### Post by zdoor on 2006-05-13
I am experiencing the same trouble. The network works but I still cannot browse. I can do email, I can do ftp to my internet provider, google works, but nothing else seems to work. I have done everything suggested on these forums:

1. Read and applied mlomker's HOW TO.
2. I have manually inserted the nameserver IP addresses in /etc/resolv.conf
3. I have added the DNS's in the networking tool
4. I have disabled IPv6 by renameing the file to *.ko.bak

Upon a cold reboot, my entries in the /etc/resolv.conf have been deleted and replaced by:

search lan
nameserver 10.0.0.38

Only difference from the previous trouble is that I am using Dapper not Breezy as Breezy does not work with SiS190.

Any help much appreciated.

---

### Post by mips on 2006-05-13
[QUOTE=zdoor]
Upon a cold reboot, my entries in the /etc/resolv.conf have been deleted and replaced by:

search lan
nameserver 10.0.0.38
[/QUOTE]


Edit your **/etc/dhcp3/dhclient.conf** file


Look for the line that reads, **prepend domain-name-servers** and add your dns server addresses to the end of that line seperated by commas. If there is an existing address their that looks like your routers or loopback interface remove it.

example:
```
prepend domain-name-servers 165.128.1.22,165.128.1.23;
```

---

### Post by zdoor on 2006-05-13
Thanks mips,

Most of the content in dhclient.conf was and is commented out by a hash #.
Only two active lines are the _prepend_ line and a line with a _request_.

Firefox still does not properly connect. It keeps "waiting" for the site. This site [www.xs4all.nl](www.xs4all.nl) is my internet provider's site. I can ping it, ftp to it and I can trace a ping to it.

Somehow, the 10.0.0.138 namerserver entry keeps coming back into the /etc/resolv.conf file even if I delete it myself before restarting. although my DNS server IP addresses are now also in this file.

---

### Post by mips on 2006-05-13
Did you edit /etc/dhcp3/dhclient.conf and add YOUR dns server addresses ?

Post your /etc/network.interface & resolv.conf files here.

Have you tried using fasterfox extension ?

---

### Post by zdoor on 2006-05-14
I do not think that fasterfox will solve this. [www.google.com](www.google.com) loads fast enough. Tracing to [www.xs4all.nl](www.xs4all.nl), shows the entire route until a certain point well beyond my computer/router/DSL modem and several other intermediate routers and takes forever from then on.

/etc/network/interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp

/etc/resolv.conf file:

search lan
nameserver 194.109.6.66
nameserver 194.109.9.99
nameserver 10.0.0.138

Nothing wrong with the two above I think, having seen the contents of other posts on this forum.

auto eth0

---

### Post by mips on 2006-05-15
Weird, your config and everything looks ok. I can open it fine, traceroute works fine.

Where does your traceroute stop ?

```
reon@obelix:~$ traceroute www.xs4all.nl
traceroute to www.xs4all.nl (194.109.6.92), 30 hops max, 40 byte packets
 1  * * *
 2  dsl-145-0-01.telkomadsl.co.za (165.145.0.1)  28.430 ms  27.528 ms  26.040 ms
 3  ndn-ip-er-1-fe-3-0-1-1.telkom-ipnet.co.za (196.43.23.197)  27.934 ms  27.495 ms  27.983 ms
 4  ny-ip-dir-globalc-pos-7-0.telkom-ipnet.co.za (196.43.9.149)  378.251 ms  377.697 ms  378.349 ms
 5  g0-2.na01.b001105-24.jfk02.atlas.cogentco.com (38.112.18.41)  382.009 ms  379.711 ms  382.112 ms
 6  g10-2-103.core01.jfk02.atlas.cogentco.com (38.112.38.165)  382.189 ms  381.727 ms  386.181 ms
 7  p15-0.core02.jfk02.atlas.cogentco.com (66.28.4.14)  430.211 ms  385.680 ms  474.272 ms
 8  p5-0.core01.ams03.atlas.cogentco.com (130.117.1.169)  468.257 ms  469.952 ms  470.079 ms
 9  t3-2.mpd01.ams03.atlas.cogentco.com (130.117.0.238)  472.228 ms  471.773 ms *
10  ams-ix.sara.xs4all.net (195.69.144.48)  452.459 ms  453.708 ms  458.289 ms
11  0.so-6-0-0.xr2.d12.xs4all.net (194.109.5.5)  454.175 ms  453.359 ms  458.242 ms
12  ab1.d12.xs4all.net (194.109.10.71)  454.228 ms  451.516 ms  454.255 ms
reon@obelix:~$
```

---

### Post by zdoor on 2006-05-16
My trace stops to [www.xs4all.nl](www.xs4all.nl) stops at the same point as yours. This does not mean that the web page loads in Firefox. It does not, or at least not in a reasonable time. The status line of Firefox very quickly changes from "Searching for ..." to "Waiting for ...". This is the case for all web pages I have tried, with the exception of Google which loads very fast all are very slow. Microsoft starts to load after some 30 secs but still takes forever to get past a blank screen.

I do not think this problem is hardware related. Perhaps you are right, and fasterfox will help. I will give it a try sometime this week.

---

### Post by mips on 2006-05-16
What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 
Look at post#4 and try Option1.

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
#4. Please post output of **cat /etc/resolv.conf**
#5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **/etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

### Post by zdoor on 2006-05-21
ADSL modem: Speedtouch 510v3 (older version)
[http://www.speedtouch.com/prod510.htm](http://www.speedtouch.com/prod510.htm)

Router: Sitecom Broadband DC207
[http://www.sitecom.com/drivers_result.php?groupid=1&productid=296](http://www.sitecom.com/drivers_result.php?groupid=1&productid=296)

Tried Post 4 Option 1 of the given thread: no luck

Output of commands/file cat's in attached file: networktrouble.txt

Ouput of Win ipconfig in attached file: ifpconfigall.txt

Sorry for the delayed response. I have been travelling.

Thanks for your efforts

---

### Post by gazzanova on 2006-05-21
In the firefox address/URL space type "about:config" , scroll down to network.dns.disableIPV6 = false ,double click this line to change it to true.
In the above do NOT type in any quotes.

---

### Post by zdoor on 2006-05-21
I have done that, it was in the thread provided by Mips. No luck. Also changed the net alias for IPv6 to off. Rebooted and tried again. Does not help. 

Only google loads fast, everything else that I have tried takes ages. Email works fine, ping works fine, I can ftp to my ISP.

ISP is XS4ALL
[http://www.xs4all.nl](http://www.xs4all.nl)

---

### Post by zdoor on 2006-05-25
Thanks for all the help received in the past week or so.

When I booted yesterday, after having had to leave it for a couple of days, to my surprise Firefox now loads all webpages with normal speed. I am not aware that I did anything different. 

It is a pity that the cause of my troubles with Firefox cannot be nailed down now. Others might have benefit from that.

I am committed to summarize my experience with Ubuntu in the first month of use. That way I hope to contribute a little bit to the development.

---

### Post by mips on 2006-05-31
Been away for 10days and only read this now.

You might find Swiftfox a better alternative to firefox.

---

