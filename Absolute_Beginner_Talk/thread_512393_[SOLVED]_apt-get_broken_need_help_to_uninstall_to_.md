---
title: "[SOLVED] apt-get broken need help to uninstall to half installed apps"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Blacksasnta on 2007-07-29
Hi all ):P
Im a newbie and I was installing some apps through Synaptic Packet Manager that went ok 
I then set up my firewall rules for tcp and udp it took all day reading and figuring it out arno iptables firewall.
I have 2 Ethernet cards and I will use one for internet sharing and the other for the internet of course.
Im not quit sure what happened but I decided to change update servers and when it went to reload the new repository list it got so far and crashed!

Unfortunately now I hane to programs half installed it tells me and im am unable to use apt-get anymore as it says I no longer have an internet connection towards the end of a best server check?
I know I done something wrong but I cant figure it out, I have tried to check config files for 2 days but got nowhere but some of them are just light years ahead of me!
I have tried recovery prompt mode with fsck -a fsck -p fsck and all is well
I dont know what information extra you would like but im more than glad to supply it!
I have looked at the network settings and they dont seem correct to me 

Route table

Destination	Gateway	Netmask	Interface
10.0.0.0	0.0.0.0	255.255.255.0	eth1
169.254.0.0	0.0.0.0	255.255.0.0	eth0
169.254.0.0	0.0.0.0	255.255.0.0	eth1
0.0.0.0	10.0.0.1	0.0.0.0	eth1
0.0.0.0	0.0.0.0	0.0.0.0	eth0
::1	::	128	lo
2001:0:53aa:64c:0:7fff:c55b:eda6	::	128	lo
2001::	::	32	teredo
fe80::ffff:ffff:ffff	::	128	lo
fe80::20f:eaff:fee7:db88	::	128	lo
fe80::	::	64	eth1
fe80::	::	64	teredo
ff00::	::	8	eth1
ff00::	::	8	teredo
::	::	0	teredo
 
Eth1 Internet

Network device:	eth1
Hardware address:	00:0f:ea:e7:db:88
IP address:	10.0.0.4
Netmask:	255.255.255.0
Broadcast:	255.255.255.255
Multicast:	Enabled
MTU:	1500
Link speed:	not available
State:	Active
Transmitted packets:	5426
Transmission errors:	0
Received packets:	5054
Reception errors:	0
Collisions:	0

Eth0 Intenet sharing not setup yet

Network device:	eth0
Hardware address:	not available
IP address:	not available
Netmask:	not available
Broadcast:	not available
Multicast:	not available
MTU:	not available
Link speed:	not available
State:	not available
Transmitted packets:	0
Transmission errors:	0
Received packets:	0
Reception errors:	0
Collisions:	0

Netstat Of All

Protocol	IP Source	Port/Service	State
tcp	0.0.0.0	4000	LISTEN
tcp	0.0.0.0	512	LISTEN
tcp	127.0.0.1	2208	LISTEN
tcp	0.0.0.0	4001	LISTEN
tcp	0.0.0.0	513	LISTEN
tcp	0.0.0.0	1	LISTEN
tcp	0.0.0.0	1025	LISTEN
tcp	0.0.0.0	993	LISTEN
tcp	0.0.0.0	20034	LISTEN
tcp	0.0.0.0	514	LISTEN
tcp	0.0.0.0	32771	LISTEN
tcp	0.0.0.0	515	LISTEN
tcp	0.0.0.0	995	LISTEN
tcp	0.0.0.0	32772	LISTEN
tcp	0.0.0.0	3140	LISTEN
tcp	0.0.0.0	40421	LISTEN
tcp	0.0.0.0	32773	LISTEN
tcp	0.0.0.0	32774	LISTEN
tcp	0.0.0.0	70	LISTEN
tcp	0.0.0.0	5190	LISTEN
tcp	0.0.0.0	44390	LISTEN
tcp	0.0.0.0	2086	LISTEN
tcp	0.0.0.0	7	LISTEN
tcp	0.0.0.0	1863	LISTEN
tcp	0.0.0.0	135	LISTEN
tcp	0.0.0.0	2087	LISTEN
tcp	0.0.0.0	1864	LISTEN
tcp	0.0.0.0	5000	LISTEN
tcp	0.0.0.0	40425	LISTEN
tcp	0.0.0.0	31337	LISTEN
tcp	0.0.0.0	9	LISTEN
tcp	0.0.0.0	138	LISTEN
tcp	0.0.0.0	42	LISTEN
tcp	0.0.0.0	6667	LISTEN
tcp	0.0.0.0	11	LISTEN
tcp	0.0.0.0	139	LISTEN
tcp	0.0.0.0	3372	LISTEN
tcp	0.0.0.0	109	LISTEN
tcp	0.0.0.0	5742	LISTEN
tcp	0.0.0.0	110	LISTEN
tcp	0.0.0.0	15	LISTEN
tcp	0.0.0.0	143	LISTEN
tcp	0.0.0.0	111	LISTEN
tcp	0.0.0.0	54320	LISTEN
tcp	0.0.0.0	6000	LISTEN
tcp	0.0.0.0	2000	LISTEN
tcp	0.0.0.0	80	LISTEN
tcp	0.0.0.0	10000	LISTEN
tcp	0.0.0.0	27665	LISTEN
tcp	0.0.0.0	6001	LISTEN
tcp	0.0.0.0	2001	LISTEN
tcp	0.0.0.0	8081	LISTEN
tcp	0.0.0.0	6129	LISTEN
tcp	0.0.0.0	465	LISTEN
tcp	0.0.0.0	8082	LISTEN
tcp	0.0.0.0	5554	LISTEN
tcp	0.0.0.0	27347	LISTEN
tcp	0.0.0.0	1524	LISTEN
tcp	0.0.0.0	17300	LISTEN
tcp	0.0.0.0	21	LISTEN
tcp	0.0.0.0	53	LISTEN
tcp	0.0.0.0	119	LISTEN
tcp	0.0.0.0	3127	LISTEN
tcp	0.0.0.0	2103	LISTEN
tcp	127.0.0.1	631	LISTEN
tcp	0.0.0.0	1080	LISTEN
tcp	0.0.0.0	12345	LISTEN
tcp	0.0.0.0	2105	LISTEN
tcp	0.0.0.0	2745	LISTEN
tcp	0.0.0.0	25	LISTEN
tcp	0.0.0.0	12346	LISTEN
tcp	127.0.0.1	9050	LISTEN
tcp	0.0.0.0	538	LISTEN
tcp	0.0.0.0	635	LISTEN
tcp	0.0.0.0	4443	LISTEN
tcp	0.0.0.0	1723	LISTEN
tcp	0.0.0.0	2107	LISTEN
tcp	0.0.0.0	443	LISTEN
tcp	0.0.0.0	49724	LISTEN
tcp	0.0.0.0	540	LISTEN
tcp	0.0.0.0	220	LISTEN
tcp	0.0.0.0	445	LISTEN
tcp	0.0.0.0	5566	LISTEN
tcp	0.0.0.0	30303	LISTEN
tcp	127.0.0.1	2207	LISTEN
tcp	0.0.0.0	1023	LISTEN
tcp6	::	2401	LISTEN
tcp6	::1	5546	LISTEN
tcp6	::	79	LISTEN
tcp6	::	53	LISTEN
tcp6	::	22	LISTEN
udp	0.0.0.0	640	
udp	0.0.0.0	512	
udp	0.0.0.0	32768	
udp	0.0.0.0	2049	
udp	0.0.0.0	641	
udp	0.0.0.0	513	
udp	0.0.0.0	1	
udp	0.0.0.0	32769	
udp	0.0.0.0	32770	
udp	0.0.0.0	32772	
udp	0.0.0.0	517	
udp	0.0.0.0	32773	
udp	0.0.0.0	32774	
udp	0.0.0.0	518	
udp	0.0.0.0	7	
udp	169.254.6.235	137	
udp	0.0.0.0	9	
udp	10.0.0.4	137	
udp	0.0.0.0	137	
udp	169.254.6.235	138	
udp	10.0.0.4	138	
udp	0.0.0.0	138	
udp	0.0.0.0	666	
udp	0.0.0.0	1434	
udp	0.0.0.0	538	
udp	127.0.0.1	161	
udp	0.0.0.0	162	
udp	0.0.0.0	2086	
udp	0.0.0.0	54321	
udp	0.0.0.0	27444	
udp	0.0.0.0	53	
udp	0.0.0.0	700	
udp	0.0.0.0	66	
udp	0.0.0.0	67	
udp	0.0.0.0	68	
udp	0.0.0.0	68	
udp	0.0.0.0	69	
udp	0.0.0.0	474	
udp	0.0.0.0	731	
udp	0.0.0.0	31335	
udp	0.0.0.0	31337	
udp	0.0.0.0	5353	
udp	0.0.0.0	111	
udp	0.0.0.0	34555	
udp	0.0.0.0	635	
udp	10.0.0.4	123	
udp	127.0.0.1	123	
udp	0.0.0.0	123	
udp6	::	512	
udp6	::	32771	
udp6	::	546	
udp6	::	546	
udp6	::	547	
udp6	::	53	
udp6	fe80::20f:eaff:fee7	123	
udp6	::1	123	
udp6	fe80::ffff:ffff:fff	123	
udp6	2001:0:53aa:64c:0:7	123	
udp6	::	123	
raw	0.0.0.0	1	7
raw	0.0.0.0	6	7
raw6	::	58	7

I dont know what else to supply that could help sovle my problem?
I have alot of apps installed and I dont wont to restart as I only have 64k connection and its taken forever to get this far!
Any help greatly appreciated:)  Thankyou [-(
cheers:)

Blacksanta

---

### Post by tomcheng76 on 2007-07-29
Can you still access the internet?
Try change the Repositories
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Blacksasnta on 2007-08-01
Solved Now!!! One way to fix it all up lol!

:) I gave up and reformatted (:
Seems too many configs and config.dats were missing?
and modem settings were wrong since corrected!

Cheers Thanks All:)

Blacksanta

---

