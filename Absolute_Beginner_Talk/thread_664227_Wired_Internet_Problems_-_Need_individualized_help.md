---
title: "Wired Internet Problems - Need individualized help"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by geekchicohio on 2008-01-10
Hi all,
I hate-hate-hate to post yet another "can't get my internet working" thread, but after reading through about a dozen threads on the topic and not really finding anything that worked, I figured it was best to try to start a new thread and get individualized help on this.

What I have:
A self-built computer (Linksys PCI ethernet card, 2.8Ghz Pentium 4, .75 gig of ram)
Ubuntu 7.04 Feisty (newish install)
A Windows (groan) PC sitting next to it with working internet (which I'm using to talk to you fine folks)
A flashdrive in case I need to put any new drivers or other packages on the Ubuntu machine

What I don't have:
The ability to connect both machines to the internet at the same time.
A PC Dual-booting Windows.

I'm using the tulip driver, and when hooked up to a live internet connection my computer requests an IP address and then tells me I'm connected to a wired network (according to the panel icon).
When I check my connection information, however, every single address listed is 0.0.0.0, speed is unknown, and my hardware address is 00:12:17:56:92:69.

lspci lists my ethernet controller as such:
```

00:0a.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev11)
```

Here's my output for:
ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:12:17:56:02:69
          inet6 addr: fe80::212:17ff:fe56:9269/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets: 5305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:1 dropped:0 pverrims:0 carrier:2
          collisions:0 txqueuelen:1000
          RX bytes:339782 (331.8kiB)  TX bytes:5194 (5.0 KiB)
          Interrupt:16 Base address: 0xd800

eth0:avah Link encap:Ethernet  JWaddr  00:12:17:56:92:69
          inet addr:169.254.5.152  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xd800

lo        Link encap: Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  mETRIC:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9868 (9.6KiB)  TX bytes: 9868 (9.6KiB)
```

sudo ifdown eth0
```

RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5618
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit httpL//www.isc/org/sw/dhcp

Listening on LPF/eth0/00:12:17:56:92:69
Sending on   LPF/eth0/00:12:17:56:92:69
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.100.1 port 67
```
sudo ifup eth0
```

There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416I
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit httpL//www.isc/org/sw/dhcp

Listening on LPF/eth0/00:12:17:56:92:69
Sending on   LPF/eth0/00:12:17:56:92:69
Sending on   Socket/fallback
DHCPDISKCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISKCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISKCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

So...thoughts?

---

### Post by buccaneere on 2008-01-10
When the panel icon lights up and says 'connected', does it say 'lo', or 'eth0'?

---

### Post by geekchicohio on 2008-01-10
When I right click on the icon and select "Connection Information" it says eth0. And displays an unknown speed, tulip driver, and ALL the addresses listed except the hardware address are all zeroes.

---

### Post by jerrynewt on 2008-01-11
Try System>Administration>Network Manager. Click on eth0 and properties. If roaming is enabled, uncheck the enable box and configure for automatic dhcp and see if it will connect then. If roaming isn't enabled go ahead and check the enable box and see if it connects then.

---

### Post by geekchicohio on 2008-01-11
It's those settings that cause it to act the way I initially described.

---

### Post by geekchicohio on 2008-01-11
I hope that last post of mine doesn't come off as rude.
I should have said from the beginning that when I use the GUI to turn on networking, specifically DHCP WIRED networking, I get the behavior described above.

---

### Post by CarrotRevelation on 2008-01-11
Could you tell us what your physical network looks like. Try not to change anything and if you absolutely must let us know in big **BOLD** letters that you've changed the physical topology.

Here's what mine would look like.

[IMG]http://img113.imageshack.us/img113/3020/netmapzf6.jpg[/IMG]
Shot at 2008-01-10
             

-Anything that doesn't say wireless is Cat 5
-Also I only have one cat 5 between my switch and router (important).

This could have been better and included I.P. address and other details. You get the picture. Help us get it too.

Right now I can see your not getting any DHCP offers from anywhere. If you have a router or your modem is getting a public I.P. from your ISP && acting as a DHCP server you can set your computers etc to static private I.P.'s consistent with your modems private I.P. address. Or you can set them to the private I.P. range of routers subnet (non-DHCP reserved).

Also I don't see why people use ifup/ifdown. I always use ifconfig and dhclient. I get more control w/ ifconfig. But when I look at your ifdown you end up releasing a 169.254 address which means your computer assigned itself an address. 

One last thing...when I look at some of your output it appears you have hand typed some of it (DHCPDISKCOVER). I this true?  The effort is appreciated but if you misstype some output we could be here forever.

Get us that map and some I.P.'s and I'm sure we can narrow this down drastically if not fix your problems.

---

### Post by geekchicohio on 2008-01-11
Hi there,
yeah, I'm hand-typing all my terminal outputs here. I'm doublechecking everything here to try to not give the illusion of a problem where there isn't one.
I think a legend with your map would have helped me, but I'll explain my network:

I've got fiberoptic TV cable coming out of the wall and going into a cable modem provided by my cable company/ISP. From there, I have Cat5 cable going into the back of the Windows machine I'm typing on. To use internet on my Ubuntu machine, I simply unplug this one, and plug in that one. Unfortunately the cable modem has only one ethernet port.

---

### Post by CarrotRevelation on 2008-01-11
Cool. I just made a pic for my netmap and got it hosted.

I'm guessing that the I.P. you usually get on your windows machine is provided by the ISP and not by your modem. So if you did ipconfig /all on your windows box you should see the DHCP provider is an I.P. belonging to your ISP.

If this is not the case and you have an I.P. address of 192.168.100.2 on your windows box I would assume your modem is handing out I.P. addresses. What's weird is that on your ifdown your ubuntu machine releases to 192.168.100.1 which means your modem is forwarding DHCP requests or handling them itself. Your Windows ipconfig /all will tell you.

Another thing to think about is if your ISP is limiting them amount of machines it will hand out adresses to by mac address. Soo...have you ever gotten online with the Ubuntu box NIC? If you havent you could always try the macchanger utility on your ubuntu box and use the windows box MAC address. I can't remember if ubuntu comes w/ macchanger. Read the manpage or "macchanger --help" option in xterm.

So. [LIST=1]
[*]We need output from ipconfig /all.
[/LIST]
      [LIST=2]
[*]We may need to try to use macchanger or load your ubuntu live cd in windows box and see if you can obtain an I.P. address. This should show whether or not the ISP is filtering.
[/LIST]

---

### Post by geekchicohio on 2008-01-11
A bit of new info, my default gateway (according to windows) is 72.240.244.1.
I can't actually navigate to this address to access controls, etc, like I'd expected to be able to, though...
The IP address for this machine is 72.240.230.112.

I did once manage to get a connection with the Ubuntu machine but the router was moved to another room without my consent, and since moving my box to where the router (and this pc) reside I've gotten nothing.

DHCP Server is 72.240.0.104
(also, DNS servers are 72.240.13.6
72.240.13.5
72.240.1.205)

---

### Post by geekchicohio on 2008-01-13
Hey all, just wanted to mention I'm still nowhere on this problem.

---

### Post by CarrotRevelation on 2008-01-16
Sorry I didn't get back to you sooner.:oops:

I just took my Gutsy cd and ran a test with modem only to make sure the distro does in fact pull an I.P. at least with Cable internet. I know that DSL uses a pppoe link...not too sure about Cable though.

If you have the Gutsy cd you should be able to bring up Ubuntu on the windows box and acquire an I.P. address. If that goes well, I would also try running the live cd on the Ubuntu box and see if you get an I.P. address. If this goes well too, it would definitely be something with the I.P. auto-configuration on the Ubuntu install. If you cannot acquire an I.P. address from the live cd on the Ubuntu box then I would assume that there is MAC filtering in place by your ISP or something wrong with the NIC. There are more tests for that situation.

With all of this I am still assuming that the router is not hooked up at all between the modem and the Ubuntu and XP machines. I wouldn't hook it up until were done testing, as this will just confuse things.

All of the 72.240.x.x I.P. addresses are owned by your ISP and you will not be able to manage them, with the exception of the one I.P. address they gave you, which is whatever box you have plugged in at the time. 

FYI & FWIW:

If you had a router plugged in, you would have your own private network of addresses that you could manage, beginning with either (192.168.x.x or 10.x.x.x or 172.16.0.0 thru 172.31.255.255). Again, you could also manage the external I.P. of the router, which would be the I.P. address given to it by the ISP. In fact your router would have at least two I.P. addresses when connected to a public network.

---

### Post by geekchicohio on 2008-01-19
After a busy few weeks myself I want to take another crack at this issue.
I'm typing this while running my feisty live CD on the windows box.
The IP address is now 72.240.202.225, which, I guess implies that I'm not limited to one or 2 through my ISP. I'm going to the live CD on the linux box now...

---

### Post by geekchicohio on 2008-01-19
Alright folks, I just plugged the ethernet cable into my linux box and tried to get online using the LiveCD. No dice.
I'm keen on blaming the tulip driver (is there an alternative I can use?) or perhaps the problem is just that Ubuntu hates me.
Thoughts?

---

### Post by geekchicohio on 2008-01-24
Progress on this problem:
I recently aquired a new Netgear Gigabit Ethernet Adapter and replaced my old card. Ubuntu is now using a different driver to run this different card and yet my situation hasn't changed.
My total lack of progress in the weeks since this started is getting pretty disheartening. I'm really not interested in using a different operating system, but I'm feeling like I'm in pretty over my head here and I can't think of any options, myself.
Anyone have any help to offer?

---

### Post by geekchicohio on 2008-01-24
Update: Based on some help I got in IRC I tried to power off and power back on the cable modem. This wasn't possible as it apparently has a battery.

---

### Post by CarrotRevelation on 2008-01-25
*Read the whole post first*

Hello,

I did have some comments. I read some of your previous posts and wasn't aware you had multiple NICS in this PC. You may want to go into BIOS and make sure they are all enabled. The whole tulip driver issue seems a little weird, but if you have the model # and other numbers of the PC I'll do some research. I'm sure you've googled the hell out of that and ubuntu. Also, the make/model and internal firmware version of your modem might help.

I had some initial thoughts like "how can we tell if the NIC drivers are misbehaving?". 
I connected a PC with Ubuntu 7.10 installed to a PC w/ Ubuntu 7.10 live CD directly together with a real hub. Obviously neither of these would receive any DHCP offers and would configure themselves with an address in the range of 169.254.x.x. I pinged them from each other. Here are my scrubbed results. 

from s3100n (the installed Ubuntu)
```
X@Workstation:~$ ifconifg
bash: ifconifg: command not found
X@Workstation:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:FC:xx:xx:xx  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79934703 (76.2 MB)  TX bytes:5947212 (5.6 MB)
          Interrupt:20 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:1B:FC:xx:xx:xx  
          inet addr:169.254.6.167  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:352 (352.0 b)  TX bytes:352 (352.0 b)

X@Workstation:~$ ping 169.254.7.177
PING 169.254.7.177 (169.254.7.177) 56(84) bytes of data.
64 bytes from 169.254.7.177: icmp_seq=1 ttl=64 time=0.119 ms
64 bytes from 169.254.7.177: icmp_seq=2 ttl=64 time=0.091 ms

--- 169.254.7.177 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.091/0.105/0.119/0.014 ms
X@Workstation:~$ arp -a
ubuntu.local (169.254.7.177) at 00:30:1B:xx:xx:xx [ether] on eth0
X@Workstation:~$ 
```

From Shuttle PC (the live Ubuntu)
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ macchanger
The program 'macchanger' is currently not installed.  You can install it by typing:
sudo apt-get install macchanger
You will have to enable component called 'universe'
bash: macchanger: command not found
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1B:xx:xx:xx  
          inet6 addr: xxxxxxxxxxxxxxxxxxxxxxxxxxx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4051 (3.9 KB)  TX bytes:5067 (4.9 KB)
          Interrupt:22 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:30:1B:xx:xx:xx  
          inet addr:169.254.7.177  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

ubuntu@ubuntu:~$ ping 169.254.6.167
PING 169.254.6.167 (169.254.6.167) 56(84) bytes of data.
64 bytes from 169.254.6.167: icmp_seq=1 ttl=64 time=2.55 ms
64 bytes from 169.254.6.167: icmp_seq=2 ttl=64 time=0.106 ms
64 bytes from 169.254.6.167: icmp_seq=3 ttl=64 time=0.102 ms

--- 169.254.6.167 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 0.102/0.922/2.559/1.157 ms
ubuntu@ubuntu:~$ arp -a
Workstation.local (169.254.6.167) at 00:1B:FC:xx:xx:xx [ether] on eth0
ubuntu@ubuntu:~$ 


```

All of this is to show that you should be able to ping from your Ubuntu installed computer to your Windows XP computer even if neither PC was able to get an I.P. address from a DHCP server. As long as they are both on the same 169.254.x.x subnet you should be able to send Pings (ICMP echo requests) and if the firewall on your XP machine doesn't drop the packets and your Ubuntu machine's driver is good you should be able to recieve PING responses (ICMP echo responses) which are written to your Xterm.

But, alas, this does not prove that your drivers and/or NIC hardware are writing DHCP packets to and from the ether correctly. So make sure your hardware topology is configured [Ubuntu PC] --> [MODEM] --> {ISP} for now.

If you have a way of installing the latest Wireshark (a.k.a. USB thumbdrive) that would be great to see what happens when you use dhclient. However, Ubuntu comes with Tcpdump. So if you can please open an terminal and

```
sudo tcpdump -D
```

...to see if you have ethX interfaces // "X" is any number.  then...
```

sudo tcpdump -i X -s 256 -vvv -w dhcp.dump
```

...to run the dump //"X" is the number preceding  any interface with "eth".  then open another terminal and run...
```

sudo dhclient
```

...to start the DHCP discovery and process. The tcpdump terminal should say Got # and the number should increase. Let it run for at least 45 seconds and hit Control + Z. Attach the dhcp.dump file when you reply or pm it to me (I've never pm'ed a file, I don't know how yet).

Also, you may be able to copy the information from a Windows "Ipconfig /all" and test them out on your Ubuntu installation. The attached file test-mod.png should explain it. On the left I have a text file copied from my XP machine that had acquired an I.P. from my ISP. On the right is where the I.P. , default gateway, and DNS should go when using the configuration thingy. Then do "sudo Ifconfig -a" in Ubuntu and copy down any HWaddr you may see for backup. Now as in red on the picture and on the same interface you configured static I.P.s do "sudo ifconfig ethX hw ether xx:xx:xx:xx:xx:xx. Which is the same MAC address as your XP machine. With the ethernet cable hooked up to the modem see if you can ping "www.google.com" If so, something fishy with the modem and your ISP is afoot.

Oh, and about resetting your modem you may be able to go in from a browser 192.168.100.1 and find a button to restart it. Maybe this kills the power for a second or two. Here's what that page on my SB5101 looks like (oh it's the surfboardcap.png)...Hmm...I just got DeJaVu...weird. Anyways let me  know.

---

