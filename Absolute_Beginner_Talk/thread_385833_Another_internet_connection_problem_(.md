---
title: "Another internet connection problem :("
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by jonathanapples on 2007-03-16
Hey all, i have recently converted a PC to Ubuntu 6.10 from XP, so i'm a little bit fragile still! This is my first Linux experience, so please be kind to me. 

I have installed Ubuntu, which seemed to go just fine, but i am having trouble connecting to the internet (using on-board network adapter).

I think the network adapter is functioning properly, but just wont connect to the router..?

My ifconfig and lshw outputs are as follows:

Hopefully i can sort this so i don't have to go back to XP!

apples@apples:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 78
       serial: 00:13:8f:52:ad:75
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine ip=58.105.28.210 multicast=yes
       resources: ioport:e800-e8ff iomemory:ff6ffc00-ff6ffcff irq:193


apples@apples:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:8F:52:AD:75  
          inet addr:58.105.28.210  Bcast:58.105.28.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe52:ad75/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25211 (24.6 KiB)  TX bytes:3125 (3.0 KiB)
          Interrupt:193 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

Any help or experience would be appreciated :)

---

### Post by oilchangeguy on 2007-03-16
make sure the network manager (the two screened icon near the clock) is set to eth0, by default it's set to lo. also you used the word router. is your modem connected directly to your computer via cable? or do you actually go thru a router? if you're connected directly to the modem have you turned it off since you installed ubuntu?

---

### Post by jonathanapples on 2007-03-16
Sorry, i do (now) have my computer directly connected to the ADSL modem. 

I did change the setting in System > Administration > Network Tools - Network Device to eth0

Was that what you meant? I dont have that icon near my clock...

---

### Post by Carlos Santiago on 2007-03-16
It seems to me that the only problem you have is concerning DNS.
To be sure, do a ping to 216.239.59.99 (thats one of the google home page IPs). 

You can also try to browse [http://216.239.59.99](http://216.239.59.99). If it shows you the google home page, then you certainly have a DNS problem.

You just have to add the IP address of your provider DNS server to the file /etc/resolv.conf

In a console (or terminal) type 

# sudo nano /etc/resolv.conf

As example
# cat /etc/resolv.conf
domain tech-faq.com
nameserver 208.25.104.7

NOTE: You have to change 'tech-faq.com' and '208.25.104.7' accordingly

---

### Post by jonathanapples on 2007-03-16
I tried manually setting the IP etc. with the same addresses that are set with my other computer that i am using to access the forums (having to unplug and re-plug in cables all the time!) to no avail.

I am unable to ping the google page (using IP address) too, which is strange.

I also enabled the connection properties icon (near the clock) and am able to see a small amount of activity (a few hundred packets of data, around 87kb received and 37kb sent).

It does seem that there is some sort of connection, but no connectivity..?

---

### Post by jonathanapples on 2007-03-16
I also cant seem to get to my modems interface page (10.1.1.1)..!!!

This is a little frustrating :(

---

### Post by jonathanapples on 2007-03-16
I also tried sudo pppoeconf, but got the following response:

             Sorry, I scanned 1 interface, but the Access            &#9474;          
          &#9474; Concentrator of your provider did not respond. Please    &#9474;          
          &#9474; check your network and modem cables. Another reason      &#9474;          
          &#9474; for the scan failure may also be another running pppoe   &#9474;          
          &#9474; process which controls the modem.

---

### Post by jonathanapples on 2007-03-17
anyone?

---

### Post by dstew on 2007-03-17
It seems from your lshw output that you were all set up. Did you change anything in your setup since then? Did you try to get to google by [http://216.239.59.99?](http://216.239.59.99?)

---

### Post by jonathanapples on 2007-03-17
That is the strange thing - from all the settings it 'should' work - but i cant ping the google IP or visit the site. or even get to the modems control panel...

i can ping the loopback 127.0.0.1 but that is the only pingable IP...

---

