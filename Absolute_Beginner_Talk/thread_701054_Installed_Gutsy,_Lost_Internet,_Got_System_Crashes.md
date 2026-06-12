---
title: "Installed Gutsy, Lost Internet, Got System Crashes"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by dwdarkstar on 2008-02-18
Hi,

  I just installed 7.10-alternate on my Averatec 3200 series.  I had Dapper on there for a while and had very few problems aside from newbie install troubles.  My ethernet connection was very reliable.  After installing Gutsy i opened Firefox and had no server.  Wanting to update my software, enable repositories, and everything else that requires a working connection, i opened my Network Settings and noticed my Wired connection had roaming mode enabled (what ever that is), and didn't seem to be working.  So i selected it and proceeded to hard code my IP address.  When i clicked Apply the system immediatley froze with my CapsLock blinking, forcing me to hard shutdown.  My Averatec has never frozen on me before.

  I have been digging in the forum for similar issues and see a few relating to wireless connection troubles; i have wireless capability but do not use it at this time.  My ethernet worked before, now it doesn't and i can't tinker with it because my system crashes.  I have included some system info below; notice there is no eth0?  Isn't that the first ethernet connection by default?  Any help would be greatly appreciated. 

pstar@Darkstar:~$ cat /proc/version
Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007
pstar@Darkstar:~$ uname -a
Linux Darkstar 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
pstar@Darkstar:~$ free
             total       used       free     shared    buffers     cached
Mem:        483324     390088      93236          0      11100     221676
-/+ buffers/cache:     157312     326012
Swap:      1317288          0    1317288
pstar@Darkstar:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:40:45:18:95:8B  
          inet6 addr: fe80::240:45ff:fe18:958b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2 overruns:0 frame:0
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xd800 

eth1:avah Link encap:Ethernet  HWaddr 00:40:45:18:95:8B  
          inet addr:169.254.6.30  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2137 (2.0 KB)  TX bytes:2137 (2.0 KB)

pstar@Darkstar:~$ ping Darkstar
PING Darkstar (127.0.1.1) 56(84) bytes of data.
64 bytes from Darkstar (127.0.1.1): icmp_seq=1 ttl=64 time=0.090 ms
64 bytes from Darkstar (127.0.1.1): icmp_seq=2 ttl=64 time=0.078 ms
64 bytes from Darkstar (127.0.1.1): icmp_seq=3 ttl=64 time=0.078 ms

--- Darkstar ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.078/0.082/0.090/0.005 ms
pstar@Darkstar:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth1
pstar@Darkstar:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
pstar@Darkstar:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.
pstar@Darkstar:~$ sudo ifup eth1:avah
Ignoring unknown interface eth1:avah=eth1:avah.
pstar@Darkstar:~$

---

### Post by jcitguy78 on 2008-02-19
are you running any other OS? Dual boot?

---

### Post by oedha on 2008-02-19
what if you code your ip in terminal
sudo ifconfig eth0 *ip_no*
sudo route add default gw *ip_no_gw*
sudo gedit /etc/resolv.conf
insert :=> *nameserver ip_dns*
then :=> sudo /etc/init.d/networking restart

---

### Post by dwdarkstar on 2008-02-19
7.10 is the only OS, no dual boot, and installed using entire disk space.

I will try ifconfig eth0 (IP) this afternoon.  Why a system freeze specific to GUI interface?  Has this been an issue with Gutsy?

---

### Post by jcitguy78 on 2008-02-19
I have not had any issues with my Gutsy, What are you running when it freezes? Apps? Games?

---

### Post by dwdarkstar on 2008-02-20
Sorry for the delay.  System freezes when configuring Networks in Administration.
Tried to configure eth0 in terminal, but I have no eth0, instead I have eth1?  Tried oedha's suggestion:

what if you code your ip in terminal
sudo ifconfig eth0 ip_no
sudo route add default gw ip_no_gw
sudo gedit /etc/resolv.conf
insert :=> nameserver ip_dns
then :=> sudo /etc/init.d/networking restart

pstar@Darkstar:~$ sudo ifconfig eth0 192.168.2.101
SIOCSIFFLAGS: No such file or directory
pstar@Darkstar:~$ sudo ifconfig eth1 192.168.2.101
pstar@Darkstar:~$ sudo route add default gw 192.168.2.1
pstar@Darkstar:~$ sudo gedit /etc/resolv.conf
pstar@Darkstar:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.
                                                                         [ OK ]

I wasn't really sure what you wanted me to do in gedit...so i changed "nameserver" to "home" and saved the gedit.file, my HD processed that for a few seconds. I may have screwed that step up.  Anyway I still have no server in Firefox.  Here is the results of ifconfig:

pstar@Darkstar:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:40:45:18:95:8B  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::240:45ff:fe18:958b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:6 overruns:0 frame:0
          TX packets:0 errors:32 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1127 (1.1 KB)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1678 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:136804 (133.5 KB)  TX bytes:136804 (133.5 KB)

See anything?  Where is eth0?  It was there before Gutsy.

---

### Post by dwdarkstar on 2008-02-20
i'm going to reinstall Gutsy but this time manually configure the network in hopes that i can avoid Network Manager.  Read up on another thread by kevdog, my eth0 is my wireless, which i have never used.  eth1 is my ethernet connection.  Wireless is a pipe-dream right now.  Maybe later.  So much capability...so little experience.

---

### Post by dwdarkstar on 2008-02-20
OK, so reinstalling Gutsy with manual network configuration did nothing.  Sooooo, hmmmmm.....  It seems as though my post has gone a bit flat.  What if these post's where like  prayers, and the Forum Staff was GOD!  You pray when you need them, but as soon as your internet is working you forget where the church is.  Ha!  right.....  Anyway, i've been hacking/slashing/googleing/bugging and i haven't really gotten anywhere.  I found a bunch of commands from a kevdog thread!  That guy is helpful, to bad my ethernet is supposed to work out of the box right?  hmmmmm......... well, i'm not working this weekend, so i guess i'll get ready for some long fruitless hours of "Up...Up.....UP.....I think we GOT IT.....AWHhhhh.  Don't got it......."  Let me end with a prayer.....

[FONT="Comic Sans MS"][CENTER][LEFT][INDENT][INDENT]Ubuntuly Father, I ask for your guidance in my hour of networking need.  Please give me the holy commands which will connect me with my brothers and sisters, and forgive my wicked computing for I know not what I do, though I am sorry for it.  As I kneel now before your pious prompt, in grace and binary, find mercy for an absolute beginner......Amend. [/INDENT][/INDENT][/LEFT][/CENTER][/FONT]

---

