---
title: "Unable to download any updates please help"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by sketchone on 2006-09-02
I recently ubuntu after switching from mandrake, im a noob when it comes to linux so i know some basics.

I managed to install and get the pc on the network to see the internet, (direct connection through a router) but i cant seem to download any updates/software, can anyone help me out - it just hangs - here is a what im getting in the terminal

sketchone@sketchone-desktop:~$ sudo gedit /etc/apt/sources.list
Password:
sketchone@sketchone-desktop:~$ wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
--12:38:55--  [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
           => `automatix-installer'
Resolving [www.getautomatix.com](www.getautomatix.com)... 1.0.0.0
Connecting to www.getautomatix.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--12:42:05--  [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
  (try: 2) => `automatix-installer'
Connecting to www.getautomatix.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--12:45:16--  [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
  (try: 3) => `automatix-installer'
Connecting to www.getautomatix.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

--12:48:28--  [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
  (try: 4) => `automatix-installer'
Connecting to www.getautomatix.com|1.0.0.0|:80...


any help will be greatly appreciated ](*,) :confused:

---

### Post by Garyu on 2006-09-02
```
wget http://www.getautomatix.com/files/automatix-installer
--13:45:58--  http://www.getautomatix.com/files/automatix-installer
           => `automatix-installer'
Slår upp www.getautomatix.com... 82.165.193.29
Ansluter till www.getautomatix.com|82.165.193.29|:80...

```
This is what you should get.

For some reason you don't get the IP right, it should be 82.165.193.29 like above. Probably a DNS settings thing. I don't know much of that though so I'm not of much help. But you should also provide a little bit more info. Like what is your hardware? What is the output of "ifconfig"?

---

### Post by sketchone on 2006-09-02
thanks for your quick reply

here are the results of "ifconfig"

sketchone@sketchone-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:E2:00:EC:CE
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:e2ff:fe00:ecce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5196822 (4.9 MiB)  TX bytes:903703 (882.5 KiB)
          Interrupt:11 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1172 (1.1 KiB)  TX bytes:1172 (1.1 KiB)

---

### Post by sketchone on 2006-09-02
anyone else able to help me out?

---

### Post by Garyu on 2006-09-02
Check out these threads:

[http://www.ubuntuforums.org/showthread.php?t=25557&highlight=dns+lookup](http://www.ubuntuforums.org/showthread.php?t=25557&highlight=dns+lookup)

what happens if you try pinging?

ping [www.ubuntu.com](www.ubuntu.com)
ping 82.165.193.29

if ping doesn't work on IP-adress there is something fundamentally wrong, not only DNS. If ping on IP-adress works but not on name then DNS is the issue. 

what is the output of
netstat -i
netstat -r

---

### Post by sketchone on 2006-09-02
both pings were successful

not sure what you mean by 

netstat -i
netstat -r

where would i find these

thanks

---

### Post by jineesh on 2006-09-02
hi
     try this
     System -> Administration -> Update Manager
     
                       jin

---

### Post by Garyu on 2006-09-02
open up a terminal and run the netstat commands. my output looks like this:
```
dan-erik@minotaur:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0
default         ax-ar01.net.kom 0.0.0.0         UG        0 0          0 eth0
dan-erik@minotaur:~$ netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0   1500 0     68335      0      0      0    62633      0      0      0 BMRU
lo    16436 0        53      0      0      0       53      0      0      0 LRU
dan-erik@minotaur:~$

```

It might give some info on your setup. Did you check out the link I gave you? It contains some info on where to look for network setup things.

Otherwise you could just try to go through the menu:
System -> Administration -> Network
There you will find your network card, so if you choose properties for that card you can see DNS server settings and add DNS servers and so on.

---

### Post by Garyu on 2006-09-02
but wait a minute... did you say that
ping [www.ubuntu.com](www.ubuntu.com)
was successful?

how about 
ping [www.getautomatix.com](www.getautomatix.com)
?

if you can ping [www.ubuntu.com](www.ubuntu.com) then your DNS should be fine. I guess you are able to surf the internet as well then? In that case, you seem to have come across some spunky stuff. If ping works, then everything else should work too...

---

### Post by sketchone on 2006-09-02
yes i was able to ping that to, yeah i have internet access with firefox and download through the browser but i cant download anything in regards to packages or update through the update managers or the software installer

---

### Post by sketchone on 2006-09-02
sketchone@sketchone-desktop:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
default         mygateway.ar7   0.0.0.0         UG        0 0          0 eth0
sketchone@sketchone-desktop:~$ netstat -i
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0   1500 0       741      0      0      0      608      0      0      0 BMRU
lo    16436 0         7      0      0      0        7      0      0      0 LRU
sketchone@sketchone-desktop:~$

---

### Post by Garyu on 2006-09-02
oh, well, if ping and firefox works then forget netstat and ifconfig and such stuff. then the problem is elsewhere. sorry, but I have to go to work now, but take a look at this site:
[http://www.mepis.org/node/10306](http://www.mepis.org/node/10306)
I know this is Mepis and not Ubuntu, but he seems to have had the same problem as you and solved it, so you should be able to pick up some hints. But I haven't got the time right now to look into it.

---

### Post by Garyu on 2006-09-02
[http://www.clarkconnect.com/forums/showflat.php?Cat=0&Number=87385&Main=86571](http://www.clarkconnect.com/forums/showflat.php?Cat=0&Number=87385&Main=86571)
this guy also had the same problem. seems like it is a router setting you need to do?

---

### Post by sketchone on 2006-09-02
> **Garyu said:**
> [http://www.clarkconnect.com/forums/showflat.php?Cat=0&Number=87385&Main=86571](http://www.clarkconnect.com/forums/showflat.php?Cat=0&Number=87385&Main=86571)
this guy also had the same problem. seems like it is a router setting you need to do?

this solved my problem thankyou very much for your help

---

