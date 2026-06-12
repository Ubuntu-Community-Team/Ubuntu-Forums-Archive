---
title: "[SOLVED] whats wrong with my network?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by rexxxlo on 2008-01-06
i am having random dropouts with my internet connection
i have a wired onboard nic
motorola surfboard 3100 modem
linksys wrt54g v3 wireless router

i can run deluge consistently for hours and get up to a 500 kib/sec speed 

then at a random time usually when i want to access the net to check email or such all activity stops dead 

if i ping the router i get this 
10 packets sent / 6 received
average speed .86ms

if i ping the modem i get this
10 sent /8 received
average speed 4.76 ms

and occasionally when i try to use Firefox to access Google i get a web page from timewarner telling me that [www.google.com](www.google.com) does not exist if i reload the page it comes up correctly

what is causing this? why does my internet access stop dead and then come back after a few minutes?

---

### Post by blueridgedog on 2008-01-06
Note a solution per say, but you could run:
```

ifconfig
```

When you are having a problem and look for errors/overruns/collisions

---

### Post by p_quarles on 2008-01-06
Couple quick things to try out. First, ping Google using its URL:
```
ping -c 8 google.com
```
Now, ping them using their IP address:
```
ping -c 8 72.14.207.99
```
Are the results different at all?

---

### Post by rexxxlo on 2008-01-06
ok of course i cant get it to happen again (makin a liar out of me)

but i do get some weird things happening 
ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:1D:7D:93:B6:21  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fe93:b621/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29002563 (27.6 MB)  TX bytes:2707456 (2.5 MB)
          Interrupt:21 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5549 (5.4 KB)  TX bytes:5549 (5.4 KB)


and the pings

>  ping -c 8 72.14.207.99
PING 72.14.207.99 (72.14.207.99) 56(84) bytes of data.
64 bytes from 72.14.207.99: icmp_seq=1 ttl=239 time=51.4 ms
64 bytes from 72.14.207.99: icmp_seq=2 ttl=239 time=52.5 ms
64 bytes from 72.14.207.99: icmp_seq=3 ttl=239 time=50.9 ms
64 bytes from 72.14.207.99: icmp_seq=5 ttl=239 time=50.0 ms
64 bytes from 72.14.207.99: icmp_seq=7 ttl=239 time=53.0 ms

--- 72.14.207.99 ping statistics ---
8 packets transmitted, 5 received, 37% packet loss, time 7008ms
rtt min/avg/max/mdev = 50.005/51.585/53.029/1.095 ms


> PING google.com (64.233.167.99) 56(84) bytes of data.
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=1 ttl=241 time=55.9 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=3 ttl=241 time=52.4 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=4 ttl=241 time=53.3 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=5 ttl=241 time=53.9 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=6 ttl=241 time=50.0 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=7 ttl=241 time=50.1 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=8 ttl=241 time=52.2 ms

--- google.com ping statistics ---
8 packets transmitted, 7 received, 12% packet loss, time 7030ms
rtt min/avg/max/mdev = 50.011/52.582/55.966/1.970 ms


i see packet loss is kinda high  what is an acceptable number for this ?

---

### Post by p_quarles on 2008-01-06
Packet loss on a good connection is 0%. Deluge would still work fine, since bittorrent is designed to deal with suspending and resuming downloads.

Based on your description of the problem, my best guess is that the problem is with something other than your computer. Either the router, the modem, or your ISP. Do you have other computers hooked up to this network? Testing for the same problem with another machine would make it easy to confirm or deny this.

---

### Post by blueridgedog on 2008-01-06
Packet loss should be 0.  If you are dropping packets, I suggest you do a traceroute and then ping each hop to see where the drop occurs.

```
james@ripstop:~$ tracepath www.google.com
 1:  ripstop.local (192.168.1.102)                          0.125ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                            asymm 106   0.894ms pmtu 1492
 2:  76-6-208-1.dhcp.embarqhsd.net (76.6.208.1)         67.397ms 
 3:  71-2-174-33.sta.embarqhsd.net (71.2.174.33)        66.878ms 
 4:  sl-gw19-rly-4-1.sprintlink.net (144.228.183.121)      70.240ms 
 5:  sl-bb23-rly-3-1.sprintlink.net (144.232.14.41)        70.453ms 
```

I would ping individually the first four hops (as that is how long it takes it to get out of my ISP and see if you can locate the error (clean pings from your pc to your router for example, but packet loss from your router to the next hop at your ISP).  The packet drop is coming from one of your hops and I bet it is your hop between your router and your ISP.

---

### Post by blueridgedog on 2008-01-06
Let me elaborate on the post above:

Fist you would ping your own interface.  192.168.1.102 in the above example.  Then your router 192.168.1.1 in the above example.  Then the interface on the end of your internet connection with your ISP, 76.6.208.1 in my case.  Then any additional hops taken at your ISP (internal routing), 71.2.174.33 in my case, finally, the first hop outside of your ISP, 144.228.183.121 in my case.

The packet loss will occur at one point and that will help you trace the problem.

---

### Post by rexxxlo on 2008-01-07
ok i did some pinging today 

my nic:10 pings 10 recieved average time .04 ms( increased after every ping )
router:10 pings 2 recieved average time .90 ms
modem:10 pings 1 recieved average time  8.42ms

then i did the recommended tracepath(thank you for this i have never seen this before)  5 or 6 times with wildly different results sometimes i could see my router sometimes not same with the modem but the thing i find strange is i can browse over to google in about 1 minute of waiting this feels like dial up 

mostly i get the response of too many hops after 31 and it stops

so i quit deluge and re ran the test 

i get about 10 hops into it and it does it again although this time it gives me more results

but no google ......it will not make it there ???

---

### Post by evil316 on 2008-01-07
The problem is either with your ethernet cable or the router.  Do the pings on a wireless machine and see what you get.  Try using a different eithernet cable between your router and NIC.  Try plugging the NIC's cable into a different port on the router .  Do pings to your router with each of these and you'll quickly diagnose the problem.

---

### Post by Papa-san on 2008-01-07
I went crazy for three weeks over the same kind of thing a while back... Messed up my box trying to 'fix' it. It turned out to be a problem with my cable provider. They fixed their stuff, and all was good. 

If this is the problem, here's the thinking:
You pay for a service, and they aren't delivering, so talk to them about it and have them fix it!.

---

### Post by rexxxlo on 2008-01-07
after a chat with tech support it seems like i will be needing a new modem i am only dociss 1.0 and they re at 2.0 now   

any recommendations on a brand ?

---

### Post by evil316 on 2008-01-07
> **rexxxlo said:**
> after a chat with tech support it seems like i will be needing a new modem i am only dociss 1.0 and they re at 2.0 now   

any recommendations on a brand ?

If you're dropping packets at the router before you even get to the modem then it's not the modem.

---

### Post by rexxxlo on 2008-01-07
i was thinking that too 

could moblock or iptables cause any of these problems?

if i try to test moblock i get this

> Trying to ping 4.2.145.239 from /etc/moblock/ipfilter.dat ...
 * MoBlock did not block the IP.
 * 
 * If you just started/reloaded MoBlock wait until it loaded completely.
 * This will be when /var/log/moblock.log shows the following line:
 * NFQUEUE: binding to queue '0'
 * 
 * 4.2.145.239 did not answer.
 * 
 * Maybe 4.2.145.239 is down/doesn't answer to pings
 * or your firewall filtered the ping.


---

### Post by evil316 on 2008-01-07
I don't know about Moblock, haven't messed with it yet.  First you need to take care of the router issue.  As I posted before, change the ethernet cable out between your PC and router and see if it clears it up.  Do any of your wireless connections have ping issues?

---

### Post by blueridgedog on 2008-01-07
> my nic:10 pings 10 recieved average time .04 ms( increased after every ping )
router:10 pings 2 recieved average time .90 ms
modem:10 pings 1 recieved average time  8.42ms

You have a bad cable, bad router or modem or a misconfiguration with one of the se devices.
> 

mostly i get the response of too many hops after 31 and it stops

The way it works is it sends out UDP packets and it can take a while which is not indicative of a problem, and there can be gaps in hops, which too is not indicative of a problem, but indicates hops that do not accept UDP packets.  Read the man page for it:  man tracepath.

> but no google ......it will not make it there ???

Many sites do not accept the packets required to make traceroute/tracepath work.

Right now you have found a problem with the equipment under your control and I would look there first.

---

### Post by blueridgedog on 2008-01-07
> **rexxxlo said:**
> i was thinking that too 

could moblock or iptables cause any of these problems?

if i try to test moblock i get this

I recommend you disable all firewalls or filtering rule while testing.

---

### Post by perlluver on 2008-01-07
I have the same router the wrt54g, I was having just about the same problem, I rebooted the router and haven't had any problems since.  Have you tried that?

---

### Post by rexxxlo on 2008-01-07
here i what i have done: 
i have tried another Ethernet cable actually a few.

i bypassed the router totally 

i have stopped moblok  

and i believe i have stopped firestarter too
 
lastly i was told by time warner that i need dociss 2.0 compatible modem


a tracepath to yahoo google would fail every time ??? so i tried yahoo
 i read somewhere while trouble shooting that some sites bock this kind of traffic and i believe google might have been one of those  but i could be wrong ? actually i i bet i am wrong  seems to be my luck lately 

here are some results now 
  
> tracepath [www.yahoo.com](www.yahoo.com)
 1:  cpe-69-207-69-173.buffalo.res.rr.com (69.207.69.173)   0.284ms pmtu 1500
 1:  no reply
 2:  gig2-1-2.buffnyntw-pe02.nyroc.rr.com (98.0.0.221)     14.337ms 
 3:  ten1-1-1.buffnyntw-pe01.nyroc.rr.com (98.0.1.109)    asymm  2  12.997ms 
 4:  ten10-2-1.buffnylkw-pe03.nyroc.rr.com (98.0.1.157)   asymm  3  14.175ms 
 5:  ten2-2-1.buffnylkw-pe01.nyroc.rr.com (98.0.1.173)    asymm  4  16.687ms 
 6:  ge-0-1-0.albynywav-rtr03.nyroc.rr.com (24.24.7.229)   21.512ms 
 7:  te-3-2.car1.Boston1.Level3.net (4.79.0.69)           asymm  6  28.251ms 
 8:  ae-11-11.car2.Boston1.Level3.net (4.69.132.246)      asymm  7  32.643ms 
 9:  ae-5-5.ebr1.NewYork1.Level3.net (4.69.132.250)       asymm  8  39.006ms 
10:  ae-91-91.csw4.NewYork1.Level3.net (4.69.134.78)      asymm  9  45.697ms 
11:  ae-93-93.ebr3.NewYork1.Level3.net (4.69.134.109)     asymm 10  39.311ms 
12:  ae-3.ebr3.Washington1.Level3.net (4.69.132.89)       asymm 11  37.029ms 
13:  ae-73-73.csw2.Washington1.Level3.net (4.69.134.166)  asymm 12  45.981ms 
14:  ae-21-79.car1.Washington1.Level3.net (4.68.17.67)    asymm 13 201.342ms 
15:  4.79.228.2 (4.79.228.2)                              asymm 11  40.327ms 
16:  so-0-0-0.pat1.pao.yahoo.com (216.115.101.128)        asymm 11 114.790ms 
17:  g-0-0-0-p150.msr2.sp1.yahoo.com (216.115.107.73)     asymm 12 111.224ms 
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500 


ifconfig
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:93:B6:21  
          inet addr:69.207.69.173  Bcast:255.255.255.255  Mask:255.255.192.0
          inet6 addr: fe80::21d:7dff:fe93:b621/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:312090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42764327 (40.7 MB)  TX bytes:6145368 (5.8 MB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6904 (6.7 KB)  TX bytes:6904 (6.7 KB)



---

### Post by evil316 on 2008-01-07
What do pings show?  A trace will usually show some servers not replying because of firewalls and stuff in the network.  Ping is what you really need to be doing right now.  Trace just needed to be run to get the address of the hops so you could find out where the ping was having problems.

---

### Post by rexxxlo on 2008-01-07
what exactly should i ping?


my nic:
 127.0.0.1 i believe this is it if when there is no router right?
10 pings no lost packets average time .08 ms

my modem:
192.168.100.1
10 pings no lost packets average time 2.81ms

yahoo.com @209.131.36.158
10 pings average time 108.27 ms

---

### Post by evil316 on 2008-01-07
sounds like your problem is fixed.  You got packet loss pinging your modem before and now you don't.  Pinging 127.0.0.1 is useless since the device is pinging itself.

---

### Post by rexxxlo on 2008-01-07
i thought all was resolved too a few hours of no problems at all  then about 10 munites ago all trafic stopped dead

the system monitor showed traffic but not much, 3.7kb/sec up and 2.6kb/s down

deluge, firefox both nothing

i did ifconfig and tracepath 
ifconfig looked normal and tracepath showed me something strange

i did tracepath to google and it tells me 

> gethostbyname2 : unknown host

i had to reboot to get any response from the network after that

---

### Post by rexxxlo on 2008-01-07
oh and now this 

tracepath

> tracepath [www.google.com](www.google.com)
 1:  send failed
     Resume: pmtu 65535 


whoops that is moblock doing that i stopped it and did a tracepath 

then i did a restart moblock and it went back to normal 

> tracepath [www.yahoo.com](www.yahoo.com)
 1:  cpe-69-207-69-173.buffalo.res.rr.com (69.207.69.173)   0.095ms pmtu 1500
 1:  no reply
 2:  gig2-1-2.buffnyntw-pe02.nyroc.rr.com (98.0.0.221)     14.739ms 
 3:  ten1-1-1.buffnyntw-pe01.nyroc.rr.com (98.0.1.109)    asymm  2  13.674ms 
 4:  ten10-2-1.buffnylkw-pe03.nyroc.rr.com (98.0.1.157)   asymm  3  12.601ms 
 5:  ten2-2-1.buffnylkw-pe01.nyroc.rr.com (98.0.1.173)    asymm  4  14.308ms 
 6:  ge-0-1-0.albynywav-rtr03.nyroc.rr.com (24.24.7.229)   51.390ms 
 7:  te-3-1.car1.Boston1.Level3.net (4.79.0.73)           asymm  6  26.836ms 
 8:  ae-11-11.car2.Boston1.Level3.net (4.69.132.246)      asymm  7  34.689ms 
 9:  ae-5-5.ebr1.NewYork1.Level3.net (4.69.132.250)       asymm  8  37.721ms 
10:  ae-91-91.csw4.NewYork1.Level3.net (4.69.134.78)      asymm  9  40.390ms 
11:  ae-93-93.ebr3.NewYork1.Level3.net (4.69.134.109)     asymm 10  40.457ms 
12:  ae-3.ebr3.Washington1.Level3.net (4.69.132.89)       asymm 11  45.188ms 
13:  ae-73-73.csw2.Washington1.Level3.net (4.69.134.166)  asymm 12  44.399ms 
14:  ae-21-79.car1.Washington1.Level3.net (4.68.17.67)    asymm 13  43.980ms 
15:  4.79.228.2 (4.79.228.2)                              asymm 11  37.072ms 
16:  so-0-0-0.pat1.pao.yahoo.com (216.115.101.128)        asymm 11 111.225ms 
17:  g-1-0-0-p140.msr1.sp1.yahoo.com (216.115.107.53)     asymm 12 111.971ms 
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500 


---

### Post by rexxxlo on 2008-01-08
i finally caught an error in ifconfig how do i go about figuring out what it is and how to prevent this from happening?

OH AND THANKS FOR PUTTING UP WITH THIS im sure it will end up being human (my) error in the end but im confused

> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:93:B6:21  
          inet addr:69.207.69.173  Bcast:255.255.255.255  Mask:255.255.192.0
          inet6 addr: fe80::21d:7dff:fe93:b621/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1667059 errors:1 dropped:0 overruns:0 frame:1
          TX packets:740690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:933857374 (890.5 MB)  TX bytes:68676548 (65.4 MB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3825 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3825 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:346400 (338.2 KB)  TX bytes:346400 (338.2 KB)



---

### Post by blueridgedog on 2008-01-08
OK, to summarize, you have intermittent loss of connectivity between your system and your modem:

> my nic:10 pings 10 recieved average time .04 ms( increased after every ping )
router:10 pings 2 recieved average time .90 ms
modem:10 pings 1 recieved average time 8.42ms


The chief error appears to be the link between your PC and your router and any upstream errors can't be concluded to be the result of things other than your first faulty link.

You have rebooted the router and replaced your Ethernet cable.

Have you tried another port on your router?

Have you tried another PC?

Do you have another Ethernet card to try?

I suggest you flood ping your router.  Here is the man entry for that:

```
       -f     Flood ping. For  every  ECHO_REQUEST  sent  a  period  ‘‘.’’  is
              printed,  while  for  ever  ECHO_REPLY  received  a backspace is
              printed.  This provides a rapid display of how many packets  are
              being  dropped.   If  interval is not given, it sets interval to
              zero and outputs packets as fast as they come back or  one  hun&#8208;
              dred  times  per second, whichever is more.  Only the super-user
              may use this option with zero interval.
```

I think it is important to turn off, permanently, all firewalling software until you have this solved.

---

### Post by rexxxlo on 2008-01-08
yes exactly, intermittent loss of connectivity

i have 
replaced the cables 
removed the router
disabled software firewall and moblock

i haven't
 seen this with other pc's s i don't really use any other pc enough warrant the test looks like i will do though 
tried another nic as mine is on board but ill dig one out and try 
 
i ran ifconfig the last time it happened and i found one tx error in the results 
i have pinged and traceroute'd yahoo and google many times with almost exact results every time
google will not finish before 31 hops and yahoo gets there in about 16-17 cant remember im at work right now and this is the home pc

i will get some new cables and see what happens and i believe i will be upgrading the modem as well just in case, they tell me dociss 1.0 is outdated and i need a dociss 2.0 modem so off to the computer store i go 

thanks for that command i will try that asap and get back to you with the results 

i wish i knew how to use vnc or ssh so i could do it from here

---

### Post by blueridgedog on 2008-01-08
To clarify, that is ping -f xxx.xxx.xxx.xxx (where xxx is an ip address), this test the link between two points.

---

### Post by rexxxlo on 2008-01-08
so strange this problem is ????

i got home from work and the network traffic is dead totally.

i tried ifconfig and traceroute nad check the system>administration>network tools
and i find another network interface,i never installed a new card or changed anything so where did it come from ?

eth0:avah

the regular eth0 is not connected and this new etho?is 

i rebooted the modem and the computer and all is back to normal .....the etho:avah is gone obviously i am connected to the net so i tried the -f ping you spoke about 

 when i do that ping should it look like this to ping my modem

> sudo ping -f 192.168.100.1

if that is correct i a full page of ..........a good thing?

i took screen shots of all of this if you would like to see any of the details?

im off to get a new modem and cat5 cables just in case too

---

### Post by blueridgedog on 2008-01-08
Each "." represents a dropped packet (not a good thing).  Pinging your local interface with the -f or your next hop should result in NO "." or dropped packets.  To whit:

My interface:
PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.
 
--- 192.168.1.102 ping statistics ---
243737 packets transmitted, 243737 received,** 0% packet loss**, time 12126ms
rtt min/avg/max/mdev = 0.003/0.004/0.947/0.005 ms, ipg/ewma 0.049/0.005 ms

My Router:
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
 
--- 192.168.1.1 ping statistics ---
35631 packets transmitted, 35631 received, **0% packet loss**, time 13642ms

So, getting a full page of "." when pinging your modem is not a good thing (I assume that the ip you listed is your modem).

I think replacing your modem is a good next step.

---

### Post by rexxxlo on 2008-01-08
ok i must have done something wrong because the new modem does that too (linksys)

what is the command i should use to ping the modem?

i used sudo ping -f 192.168.100.1 

that is the address i use to get in to the modem web interface  so that should be the address i use to ping ,right?

when i do this i get ......as fast as they can go it will fill the screen in about 1-2 min

---

### Post by blueridgedog on 2008-01-08
Ok, two different modems, two different Ethernet cables and still substantial packet loss (you did not post the loss, but once you pres CTR+C to kill the ping, it should give you a summary like I posted).

I must admit that this would probably be a 10 second problem if we were in the same room, but the forum is rather iterative. 

You still have a failure between your PC and the modem.  It can at this point be hardware (nic card) or configuration.  Lets look at your configuration.

Your modem is 192.168.100.1 and connects to the cable LAN

Your PC is (guessing) 192.168.100.2 and connects to the modem.

Confirm that 

```
sudo ping -f 192.168.100.2 (or what ever your local IP address is)
```

is clean.  If it is not clean, post the summary after you use CRT+C.

Run 

```
sudo ping -f 192.168.100.1
``` 

for 15 seconds, then use CRT+C to end it and post the summary.

Post the output of the command:

```
route
```

And post the output of:
```

cat /etc/network/interfaces 
```

We will get there.

---

### Post by rexxxlo on 2008-01-09
i totally understand that and i hate when a new page starts sometimes i don't see it right away 

its weird there isn't  total failure i am getting a constant 250kb/sec dl speeds on deluge right now

i didnt know about control+c  so thats my fault

ok here goes 


> 192.168.100.1 ping statistics ---
925 packets transmitted, 114 received, 87% packet loss, time 10962ms
rtt min/avg/max/mdev = 2.050/2.146/2.628/0.096 ms, ipg/ewma 11.863/2.158 ms


route

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


cat /etc/network/interfaces
> auto lo
iface lo inet loopback



i hope this is correct

---

### Post by rexxxlo on 2008-01-09
you know what let me add/change that i had the router in line i redid it with out the router inline

> 192.168.100.1 ping statistics ---
460 packets transmitted, 55 received, 88% packet loss, time 5086ms
rtt min/avg/max/mdev = 1.089/1.157/1.662/0.104 ms, ipg/ewma 11.081/1.132 ms
lolo@lolo-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
69.207.64.0     *               255.255.192.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         cable1-0.buffny 0.0.0.0         UG    0      0        0 eth0
lolo@lolo-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback



---

### Post by airtonix on 2008-01-09
pardon my ignorance, but maybe your nic is borked?

for your /etc/network/interfaces should at least have something like : 

> auto eth0
iface eth0 inet static
address 192.168.100.2
netmask 255.255.255.0
gateway 192.168.100.1


the portion you posted about your existing  /etc/network/interfaces as : 
>  			 				auto lo
iface lo inet loopback
is defining the local loop back interface, ie 127.0.0.1

---

### Post by rexxxlo on 2008-01-09
i have been thinking that too but i can get a good connection most of the time sometimes it will just die for no reason 

i thought it was my router ...nope,modem ....i bought a new one  so thats not it 

although i have had the problem where sometimes when i start the computer the eth0 does not work and there is a mysterious etho:avah in the network devices that if you try to configure it tells you that it does not exist ???

it even shows up in ifconfig with the same mac id as the eth0

i have googled this and didnt seem to find anything other than eth0:avah is a nic  but i dont have it so why is it showing up?

---

### Post by airtonix on 2008-01-09
open your network gui, and look for the domain/workgroup name panel.

is avahi turned on? this will be causing some problems.

ps: avahi = bonjour = suxor

---

### Post by rexxxlo on 2008-01-09
im not sure i understand this 

the network giu ?

system>administration>network?
there is no area in there that says anything about avhi

system>administration>network tools 
again  nothing about avhi

---

### Post by blueridgedog on 2008-01-09
Your posting implies that your router is:
```

default 192.168.1.1 0.0.0.0 UG 0 0 0 eth0
```

But in our conversation you imply that you are not using 192.168.1.1 for your modem, but 192.168.100.1.  Your system can either be on the 192.168.100.0/255 subnet or the 192.168.1.0/255 subnet, but not both.

My suspicion is further raised by looking back at your other posts where you gave us/me and ifconfig output:

```

eth0 Link encap:Ethernet HWaddr 00:1D:7D:93:B6:21
inet addr:**192.168.1.100** Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::21d:7dff:fe93:b621/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:29481 errors:0 dropped:0 overruns:0 frame:0
TX packets:28826 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:29002563 (27.6 MB) TX bytes:2707456 (2.5 MB)
Interrupt:21 Base address:0x6000 
```

So, you may simply have a configuration problem and this could simply be that you router/modem were on 192.168.100.XXX and your PC/router were on 192.168.1.XXX.

Lets determine what you have.  Post a screenshot of your network setup screen (see mine) showing your interfaces the detail for eth0.

I can't make out the results of your route command as it obfuscated the IP:

```
lolo@lolo-desktop:~$ route
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
69.207.64.0 * 255.255.192.0 U 0 0 0 eth0
link-local * 255.255.0.0 U 1000 0 0 eth0
default cable1-0.buffny 0.0.0.0 UG 0 0 0 eth0
```

Try route -n so I can see what it things is a default route in IP speak rather than cable1-0.buffny.

My current take on this is that things are misconfigured, but I may be wrong.

---

### Post by rexxxlo on 2008-01-09
i see that your configuration does not use roaming mode but mine does it worked in the past so i never messed with it anyways here it is

---

### Post by blueridgedog on 2008-01-09
How about the

```
route -n
```

---

### Post by rexxxlo on 2008-01-09
it is the top left corner or this one is the same

>  route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
69.207.64.0     0.0.0.0         255.255.192.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         69.207.64.1     0.0.0.0         UG    0      0        0 eth0


---

### Post by blueridgedog on 2008-01-10
I think I have been chasing a fantoom. 

Your PC is now 192.168.1.100
Your modem is now 192.168.1.1
Your router WAS 192.168.100.1 but you removed it
When your router was in the loop, I suspect your PC was something like 192.168.100.XXX

So getting errors at this point pinging a router that is unplugged and unconnected is not tell us much.

If you only have your PC and your modem in the loop at this point, confirm this so we can clear our understanding.

---

### Post by rexxxlo on 2008-01-10
yes only modem and computer 

sorry once in there i did do some of those things with the router in the chain right after i bought the new router but it is 192.168.1.1 now and always was 
and the modem is 192.168.100.1 and always was 
those have stayed the same sorry for the confusion

sorry i made the mistake in post 32 and fixed it in 33 i should have just edited post 32 but i was not sure if you read it yet  its bad enough that i have made a disaster of my network but i have confused the guy helping me is even more of an embarrassment please excuse me

---

### Post by blueridgedog on 2008-01-10
OK, let's start fresh.

I assume:

Your PC is now 192.168.1.100
Your modem is now 192.168.1.1

If this is wrong, let me know and adjust the numbers below accordingly.

Let's ping your pc and modem aggresively:

ping -f 192.168.1.100

let it run a bit and then end with CTRL+C and post the summary.

ping -f 192.168.1.1

Like above, let it run a bit and then end with CTRL+C and post the summary.

I bet it will be clean.

---

### Post by rexxxlo on 2008-01-10
ok nice as soon as i get home from work i will do that

oh typo sorry about that 
router 192.168.1.1
modem 192.160.100.1

---

### Post by blueridgedog on 2008-01-10
> **rexxxlo said:**
> ok nice as soon as i get home from work i will do that

oh typo sorry about that 
router 192.168.1.1
modem 192.160.100.1

Lets leave the router our for the time being and just clarify your PC and Modem IP address.  Do you really mean "160" above?

---

### Post by rexxxlo on 2008-01-10
no 168 im sorry  i have the asus eee and typing on it is a real challenge sometimes:):):)

ok here it goes ready this is going to shock you 88% loss again????

> lolo@lolo-desktop:~$ sudo ping -f 192.168.100.1
PING 192.168.100.1 (192.168.100.1) 56(84) bytes of data.
(i removed the dots )........
--- 192.168.100.1 ping statistics ---
576 packets transmitted, 66 received, 88% packet loss, time 6197ms
rtt min/avg/max/mdev = 1.071/1.176/1.846/0.164 ms, ipg/ewma 10.779/1.147 ms
lolo@lolo-desktop:~$ 




---

### Post by rexxxlo on 2008-01-10
i did an ifconfig in another console during the pinging and i get no errors at all


i was thinking that my bandwidth usage might have been the culprit but as you see i used quite a bit today and it was still connected when i got home from work 

> lolo@lolo-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:93:B6:21  
          inet addr:69.207.69.173  Bcast:255.255.255.255  Mask:255.255.192.0
          inet6 addr: fe80::21d:7dff:fe93:b621/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18755594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11815569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15573936503 (14.5 GB)  TX bytes:1791016091 (1.6 GB)
          Interrupt:21 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82767 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9910099 (9.4 MB)  TX bytes:9910099 (9.4 MB)


---

### Post by blueridgedog on 2008-01-10
Here is the problem I keep running back to:

Your interface:

eth0 Link encap:Ethernet HWaddr 00:1D:7D:93:B6:21
inet addr:**69.207.69.173** Bcast:255.255.255.255 Mask:255.255.192.0
inet6 addr: fe80::21d:7dff:fe93:b621/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:18755594 errors:0 dropped:0 overruns:0 frame:0
TX packets:11815569 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:15573936503 (14.5 GB) TX bytes:1791016091 (1.6 GB)
Interrupt:21 Base address:0x6000 

Your modem is at** 192.168.100.1**.

I think the test is producing bogus results because the address of the modem and the address it gives out to your PC via dhcp are not on the same subntet.

Your computer has an ip that appears to be a road runner cable modem in Buffalo or Syracuse.

69.207.69.173 PTR record: cpe-69-207-69-173.buffalo.res.rr.com. [TTL 86400s] [A=69.207.69.173]

Give me the the output of ```
route -n
``` again and lets ping -f the gateway device to test the link.

---

### Post by rexxxlo on 2008-01-10
lolo@lolo-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
69.207.64.0     0.0.0.0         255.255.192.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         69.207.64.1     0.0.0.0         UG    0      0

---

### Post by rexxxlo on 2008-01-10
sudo ping -f 69.207.69.173
PING 69.207.69.173 (69.207.69.173) 56(84) bytes of data.
 
--- 69.207.69.173 ping statistics ---
320376 packets transmitted, 320376 received, 0% packet loss, time 9405ms
rtt min/avg/max/mdev = 0.008/0.010/8.067/0.015 ms, ipg/ewma 0.029/0.010 ms
lolo@lolo-desktop:~$

---

### Post by rexxxlo on 2008-01-10
i looked at that screenshot you attached and mine is nowhere near that 

are you using a router?

and when you setup a static ip address did you use the gui or is there a code that does it for you  ?

i tried tto do what you have in your screenshot i even put my router in, and before i changed it everything worked but when i took roaming mode and turned it off to configure it like yours is it shuts down the network 

set it backup to roaming mode and all is fine

oh and the same 88% packet loss as before i am going to try the nic now and see what happens

---

### Post by CarrotRevelation on 2008-01-11
I hate to butt in, but I feel I have too. I work at a help desk and I have some observations.

1. Rule #1 where is the network map? There is confusion on the physical topology of the network. That needs to be resolved and under no circumstances shall any of the cables or appliances be moved during troubleshooting unless the expert says to do it.

2. Rule #2 Determine the logical topology. Run the commands and copy and paste the output. Avoid at all costs retyping the output in the thread.

I see Blueridgedog is trying to move methodically through each link, but thats hard to do if the physical topology gets changed.

I notice that on one point (pg. 5 I believe) Blue asks Rexxxlo to ping 192.168.1.1 which is later identified as the router. The results are never posted. And I believe that is because the router is not there (pg. 6 Rexxxlo, you say that you even try putting the router back in). If the router wasn't in-line then you should have said that when Blue asked you to ping 192.168.1.1. 

If the router *was* in the picture and you are still getting a public I.P. on your computer from the ISP(69.207.69.173) there is something wrong w/ the DHCP process on your router, the DHCP service on your router is turned off, or the DHCP service on your router is set to forward DHCP requests to your modem, which forwards them to your ISP. I highly doubt this paragraph is the case.

Rexxxlo, I mean no disrespect, but let Blue know your physical setup and do not change it unless told to do so. It's easier to help someone who knows absolutely nothing than someone who kinda knows something. Again sorry to butt in.

I'll be watching w/ CarrotEyez! :grin:

---

### Post by rexxxlo on 2008-01-11
i totally understand im not too good at networking and such so this could be my fault totally 

how about this i can start over ?

back a page or so the router was i there during one test but i removed it right after and redid th test it was in because i bought my new modem and was fooling around thinking he modem might have caused the problems all along and i could just go back to normal

so i will recap 
i am having random dropouts in connectivity
my router had been removed  to rule it out, the modem has been replaced now too the ip remained the same though
the ip for the modem is 192.168.100.1
the ip for the router  is 192.168.1.1 (witch i removed)

post 39 has the screenshot with the results of   route -n  and the remaining info on my network connections  


i edited this post and included said screenshot

---

### Post by blueridgedog on 2008-01-12
OK, with the new information posted, it appears with just a pc and a modem you end up with these two things:

A PC at: 69.207.69.173
(do an ifconfig to verify this, as it may have changed with dhcp)

And a gateway at: 69.207.64.1 (as shown buy the route -n).

So, the first real step is to ping -f each of these for a good ten seconds and see what the loss ratio is (if any).

---

### Post by blueridgedog on 2008-01-12
Lets use Carrot's comments for a 10,000 foot view of the problem.  

You have intermittent problems.  We want to test those problems by looking at each link in the chain.

I assume at this point that you have a PC connected to a cable modem.

The first item to do is put IP addresses with each device.

ifconfig will give you the IP of your Ethernet interface.

route -n will give you the IP address of your next hop (I suspect that is at the cable company's head end, on the other side of the cable system).

Once you have those two IP's, and the first one may change, so you need to check it before you test, you can do some mild and not-so-mild testing.

I like to use "ping -f XXX.XXX.XXX.XXX" to stress a link and give me a quick down and dirty overview of the condition.

If you local network (your LAN so to speak) is clean, but you get packet loss to the next hop, then you call the ISP with the technical data (I get XX% packet loss to my gateway between 8:00pm and 11:00pm etc etc).

But, if these test are clean, then we need to look else ware or setup some automated testing (It took me months one time to get enough MRTG graphs of ping loss to prove to a cable company that there was an RF problem at certain times of the day).

---

### Post by rexxxlo on 2008-01-15
sorry it took me so long to respond life happened, ya know.

so back to it 

i have done the requested things you asked for and i have results as follows

ifonfig
> lolo@lolo-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:93:B6:21  
          inet addr:69.207.111.90  Bcast:255.255.255.255  Mask:255.255.192.0
          inet6 addr: fe80::21d:7dff:fe93:b621/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20087 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9967304 (9.5 MB)  TX bytes:2106243 (2.0 MB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15353622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15353622 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1289769367 (1.2 GB)  TX bytes:1289769367 (1.2 GB)


route -n
> lolo@lolo-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
69.207.64.0     0.0.0.0         255.255.192.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         69.207.64.1     0.0.0.0         UG    0      0        0 eth0


sudo ping -f 

> lolo@lolo-desktop:~$ sudo ping -f 69.207.111.90
[sudo] password for lolo:
PING 69.207.111.90 (69.207.111.90) 56(84) bytes of data.
. 
--- 69.207.111.90 ping statistics ---
10596490 packets transmitted, 10596490 received, 0% packet loss, time 251652ms
rtt min/avg/max/mdev = 0.008/0.009/8.689/0.005 ms, pipe 2, ipg/ewma 0.023/0.009 ms


and 

> 
69.207.64.1 ping statistics ---
15299 packets transmitted, 1877 received, 87% packet loss, time 301739ms
rtt min/avg/max/mdev = 6.139/14.145/134.181/8.012 ms, pipe 12, ipg/ewma 19.724/13.276 ms




i think my nic is faulty or not configured correctly ?

---

### Post by blueridgedog on 2008-01-15
> 69.207.64.1 ping statistics ---
15299 packets transmitted, 1877 received, 87% packet loss, time 301739ms
rtt min/avg/max/mdev = 6.139/14.145/134.181/8.012 ms, pipe 12, ipg/ewma 19.724/13.276 ms

This is your next hope gateway, it is more than likely the router at the cable company head end.  My next step would be to call the cable company tech support and state that you have substantial packet loss when pinging your gateway and that you suspect that you have a noisy drop or that your are in a noisy node.  You can further report that you have tried a different modem.

Also, I suspect you could reproduce this error regardless of OS or computer (It would be nice if you had one to try).

I helped deploy the second cable modem internet setup in the US in 1994, and this looks like a classic case of noisy node/drop.

---

### Post by rexxxlo on 2008-01-16
from my eee

> 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
69.207.64.0     0.0.0.0         255.255.192.0   U     10     0        0 eth0
0.0.0.0         69.207.64.1     0.0.0.0         UG    10     0        0 eth0
/home/user> sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1E:8C:3D:AB:09
          inet addr:69.207.80.250  Bcast:255.255.255.255  Mask:255.255.192.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6899 errors:0 dropped:0 overruns:0 frame:0
          TX packets:523 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:711556 (694.8 KiB)  TX bytes:0 (0.0 b)
          Memory:fbfc0000-fc000000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1956 (1.9 KiB)  TX bytes:1956 (1.9 KiB)

/home/user> sudo ping -f 69.207.64.0
Do you want to ping broadcast? Then -b
/home/user> sudo ping -f 69.207.64.1
PING 69.207.64.1 (69.207.64.1) 56(84) bytes of data.

--- 69.207.64.1 ping statistics ---
4181 packets transmitted, 4181 received, 0% packet loss, time 44026ms
rtt min/avg/max/mdev = 6.071/11.754/57.372/5.195 ms, pipe 4, ipg/ewma 10.532/10.230 ms
/home/user> sudo ping -f 69.207.80.250
PING 69.207.80.250 (69.207.80.250) 56(84) bytes of data.

--- 69.207.80.250 ping statistics ---
123345 packets transmitted, 123345 received, 0% packet loss, time 40035ms
rtt min/avg/max/mdev = 0.018/0.023/100.203/0.285 ms, pipe 2, ipg/ewma 0.324/0.023 ms


---

### Post by blueridgedog on 2008-01-16
If it comes and goes, then I think for certain that it is noisy RF.

---

### Post by rexxxlo on 2008-01-16
if i use another computer it gives 0% loss if i use this one i get 88% every time router or no router, new modem or old modem 



> lolo@lolo-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
69.207.64.0     0.0.0.0         255.255.192.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         69.207.64.1     0.0.0.0         UG    0      0        0 eth0
lolo@lolo-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:7D:93:B6:21  
          inet addr:69.207.111.90  Bcast:255.255.255.255  Mask:255.255.192.0
          inet6 addr: fe80::21d:7dff:fe93:b621/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4747358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3560448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:879932190 (839.1 MB)  TX bytes:4120565510 (3.8 GB)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21238575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21238575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1785659739 (1.6 GB)  TX bytes:1785659739 (1.6 GB)

lolo@lolo-desktop:~$ sudo ping -f  69.207.64.1
[sudo] password for lolo:
PING 69.207.64.1 (69.207.64.1) 56(84) bytes of data.
...........................................................................................................................................................................................................
--- 69.207.64.1 ping statistics ---
233 packets transmitted, 30 received, 87% packet loss, time 2929ms
rtt min/avg/max/mdev = 47.081/306.730/451.176/124.893 ms, pipe 36, ipg/ewma 12.627/195.968 ms
lolo@lolo-desktop:~$ sudo ping -f  69.207.111.90
PING 69.207.111.90 (69.207.111.90) 56(84) bytes of data.
 
--- 69.207.111.90 ping statistics ---
760081 packets transmitted, 760081 received, 0% packet loss, time 15637ms
rtt min/avg/max/mdev = 0.008/0.009/1.344/0.006 ms, ipg/ewma 0.020/0.009 ms
lolo@lolo-desktop:~$ 




---

### Post by rexxxlo on 2008-01-16
i swapped a pci network card in to the machine and shut the other one off in the bios

> lolo@lolo-desktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:11:95:66:5C:DB  
          inet addr:69.207.123.118  Bcast:255.255.255.255  Mask:255.255.192.0
          inet6 addr: fe80::211:95ff:fe66:5cdb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1709909 (1.6 MB)  TX bytes:369999 (361.3 KB)
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1977779 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1977779 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:166144393 (158.4 MB)  TX bytes:166144393 (158.4 MB)

lolo@lolo-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
69.207.64.0     0.0.0.0         255.255.192.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         69.207.64.1     0.0.0.0         UG    0      0        0 eth1
lolo@lolo-desktop:~$ sudo ping -f  69.207.64.1
PING 69.207.64.1 (69.207.64.1) 56(84) bytes of data.
.    
--- 69.207.64.1 ping statistics ---
1646 packets transmitted, 1645 received, 0% packet loss, time 17022ms
rtt min/avg/max/mdev = 6.363/11.848/51.422/5.360 ms, pipe 5, ipg/ewma 10.347/11.180 ms
lolo@lolo-desktop:~$ sudo ping -f  69.207.123.118
PING 69.207.123.118 (69.207.123.118) 56(84) bytes of data.
 
--- 69.207.123.118 ping statistics ---
377942 packets transmitted, 377942 received, 0% packet loss, time 7966ms
rtt min/avg/max/mdev = 0.008/0.009/1.860/0.008 ms, ipg/ewma 0.021/0.009 ms
lolo@lolo-desktop:~$ 




looks like it was the nic all along ??? sorry about that i should have swapped it out before even posting but this is a brand new mobo 

is there a way test it or is it not configured correctly or something because it gave me that 87-89% loss consistently every time i pinged it 
the chipset and video card were onboard and made by nvidia 

i stopped using the onboard  vga and went to a pci card so i have the onboard disabled could that be a problem ?

---

### Post by rexxxlo on 2008-01-16
i changed the nic redid all of the above tests with the new ip address's and i get 0% packet loss 


strange the onboard video and nic are not a recognized part or something 

xorg will not recognize the video card and the continous packet loss drove me crazy 

with the pci cards all is fine even with the router in the chain i think this is  solved too bad  it took me 7 pages to figure out my nic is messed up


thanks for all that helped if you have any ideas or other tests that i don't know or didn't try please tell me id like to try and i will check on this thread

---

### Post by Vanquish86 on 2008-01-16
First thing I learned when troubleshooting a home network:

If you have other similar hardware available, swap it out and test it on that first. Could save you a lot of time and effort. Although, as was stated earlier in the thread, this could have been a 10 second problem if you two were both in the same room.

---

### Post by rexxxlo on 2008-01-17
yea or it could have been a 10 second resolution if i used my noggin too though haha!


the things you learn the hard way are more fulfilling sometimes

---

### Post by nikoPSK on 2008-01-17
have your troubles been solved? Then please mark this thread as "SOLVED".

nikoPSK

---

