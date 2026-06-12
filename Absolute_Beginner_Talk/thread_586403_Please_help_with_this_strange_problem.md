---
title: "Please help with this strange problem"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by chigsy on 2007-10-22
I have had a scan through the forums and could not find anything similar to my problem (sorry if there is one).
PC = ASUS Terminator 2 AE1  barebones. AMD 64bit socket 754 3100 Sempron. 1GB Corsair ram. 80GB SATA HDD. Mobo chipset SIS  North Bridge 760GX South Bridge 965L. Runs XP home.

First of all i downloaded Gutsy and tried it "live". Looked great, except i could not use firefox. i thought O, no internet. Not so. I could use the google search bar no problem at all!?. But whatever i searched for, i could not go to. Hmmm. Tried installing, it froze at 82% scanning the mirror? apt get i think. Corrected mbr etc  and started again. Downloaded 7.04 32bit. Same problem. Google toolbar works fine, with results for my search query every time. Click on one and no go. Ping works ok??. I hope someone can give me a pointer in the right direction. Many thanks. Oops, i also downloaded Open Suse, with the same problem. It stops when trying the net. Windows works fine online. I'm confused :(

---

### Post by realvz on 2007-10-22
can you try opera browser?
but if you have no internet how will you donwload it?

---

### Post by forestpixie on 2007-10-22
what are you using to connect to hte net

---

### Post by offroad64 on 2007-10-22
I had the same problem on the weekend when I did an upgrade to 7.10 on my daughters computer. There is a problem with one of the US mirrors.Wait till it hangs. Then here is a quick fix to this issue, disable your network devices and it will time out within 30secounds and proceed with the install. Just enable your network after that and everything should be fine. Worked like a charm.

---

### Post by chigsy on 2007-10-22
I have a broadband connection. I connect through a netgear router (wired) but did connect straight to the cable modem in case it was the router causing the problem. No idea how i would get Opera on. I no nothing about Linux, never mind Ubuntu. But will try to learn as fast as possible. Anything to ditch windoze. Thanks again.

---

### Post by realvz on 2007-10-22
try changing your repositories
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by tact on 2007-10-22
Well I suppose you gotta take things one step at a time.

1.  Boot from the LiveCD and wait...wait...wait... til the desktop finishes loading.  Network manager should be loaded and you can right click on that icon, then click on connection information.

Can you copy down the result and post here.

2.  Click on Applications>Accessories>Terminal and at the command prompt type
```
ifconfig
```

Then copy the result back to us here.

3.  What do you know about your home network?  Is your netgear router giving out IP addresses as a DHCP server?  

Thats a start

---

### Post by chigsy on 2007-10-22
OK folks, Thanks for the info. I will try install again, later today. Just a bit concerned that firefox wouldnt go to say [www.bbc.co.uk](www.bbc.co.uk), or for that matter anywhere else, even in live cd. Will let you know how i get on. Many many thanks for your help.

---

### Post by chigsy on 2007-10-22
Hi again
More info
From live cd typed ifconfig as instructed

eth0    Link encap:Ethernet HWaddr 00:13:D4:0C:41:E2
            inet addr:192.168.1.4 Bcast:192.168.1.255 Mask:255.255.255.0
            inet6 addr: fe80::213:d4ff:fe0c:41e2/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets: 239 errors:0 dropped:0 overruns:0 frame:0
            TX packets: 248 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:16844 (16.4KB)  TX bytes:18152 (17.7KB)
            Interrupt:19 Base address:0xdead

Lo        Link encap: Local Loopback
            inet addr:127.0.0.1 Mask:255.0.0.0
            inet6 addr:  ::1/128 Scope:Host
            UP LOOPBACK RUNNING MTU:16436 Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:0 (0.0b)  TX bytes:0 (0.0b)

I hope this is of some use. Many thanks

---

### Post by habtish on 2007-10-22
Might be a DNS problem... not sure though. It looks like you are behind a router. Connect to your router(192.168.1.1) and see what the DNS namer servers are (status tab on a linksys router). In the terminal type ```
 cat /etc/resolv.conf 
``` and see if the nameserver/s match what your router has listed.... but then again.. since you said you could ping... I think I am wrong on the DNS idea.... can you ping google.com? or are you pingning an ip (123.45.678.9)?

---

### Post by chigsy on 2007-10-22
Hi
I have had the same problem plugged straight into the cable modem. In the router it says DNS Address, get automatically from ISP. Any good?

---

### Post by habtish on 2007-10-22
Try pinging a domain to see if it is a DNS problem in the first place. ```
 ping -c 3 www.google.com

``` 

if you get a ping reply then it is a different matter

---

### Post by chigsy on 2007-10-22
Hi again :)
I went in system>Admin>Network tools>Ping and typed [www.google.com](www.google.com). The results are
Round trip time stats. Min 25.60ms Average 57.35ms Max 119.00ms. Transmission statistics. Packets Transmitted 5 Received 5 Successful packets 100%. Any good???? As ever, many thanks to you all.

---

### Post by chigsy on 2007-10-22
The plot thickens???? as i am posting this from firefox, from Ubuntu Gutsy, through the same router and modem, but on another PC. Worked first time. Why o why on earth will my other PC not work :(. It works fine in Windoze. Very strange indeed

---

### Post by chigsy on 2007-10-23
I am starting to think its the motherboard/chipset. I cannot think of anything else. As i said i tested Ubuntu last night on an old shuttle mobo, duron 1000 and 512MB of ram. It ran sweet as, through the same connection the Asus T2 will not work through. Any last ideas folks. As ever, many thanks.

---

### Post by realvz on 2007-10-23
if possible...maybe try and use this machine with somebody else's internet connection...

chances are it wont work...but lets just try and get network issues away

---

### Post by chigsy on 2007-10-23
Thanks for the reply :) Yes i can get that done. Great idea. Shouldnt take to long either. Will report findings asap. Thanks again

---

### Post by chigsy on 2007-10-23
Hi all. Tested on friends cable modem. No good. Exact same problem. Tested as live cd and in install. Mmmmm. Motherboard/chipset. What else could it be??.... Many thanks for reading. All help/advice appreciated.

---

### Post by chigsy on 2007-10-24
Perhaps if i got hold of a network card, that would eliminate another area (after turning the onboard one off). Just starting to lose hart :(  Any other ideas appreciated. Many thanks

---

### Post by chigsy on 2007-10-24
Lol, forget network card idea. As i stated i can use google search etc, so HOW can it be the network card. tut. .... help

---

### Post by Mischa on 2007-10-24
try this as root: (sudo su -)

vi /etc/sysctl.conf

add the following two lines

net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760

sysctl -p

see [http://inodes.org/blog/2006/09/06/tc...d-kernel-2617/]("http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/") for an excellent explanation

---

### Post by gabizu on 2007-10-25
hi! i have this problem too but i think that my problem is my network proxy! how i can set the proxy before the instalation? pls help

---

