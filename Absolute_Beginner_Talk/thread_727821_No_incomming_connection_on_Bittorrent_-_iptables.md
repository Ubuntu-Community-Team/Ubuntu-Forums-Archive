---
title: "No incomming connection on Bittorrent - iptables?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by thomas7.10 on 2008-03-18
Hi!

I got my PC running as a router under a couple of weeks and under that time the Bittorent thing was just working. I was using Firestarter and somehow i got it to work. Now I've got a linksys router and I'm using Tomato on it.. Now both bittorent clients i tired to use say that they can't no incoming connection. Can maybe someone help me with that? The ports I'm using for bittorrent are between 54898 and 54912. I tried to open these but it doesn't seem to work Here is the iptables list from my router:

```

Tomato v1.17.1385


BusyBox v1.2.2 (2008.02.26-13:57+0000) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

# iptables --list
Chain INPUT (policy DROP)
target     prot opt source               destination         
DROP       0    --  anywhere             anywhere            state INVALID 
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     igmp --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
DROP       0    --  anywhere             anywhere            state INVALID 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN tcpmss match 1461:65535 TCPMSS set 1460 
L7in       0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
wanin      0    --  anywhere             anywhere            
wanout     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            
upnp       0    --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain L7in (1 references)
target     prot opt source               destination         
RETURN     0    --  anywhere             anywhere            LAYER7 l7proto skypetoskype 
RETURN     0    --  anywhere             anywhere            LAYER7 l7proto skypeout 
RETURN     0    --  anywhere             anywhere            LAYER7 l7proto sip 
RETURN     0    --  anywhere             anywhere            LAYER7 l7proto edonkey 
RETURN     0    --  anywhere             anywhere            LAYER7 l7proto h323 
RETURN     0    --  anywhere             anywhere            LAYER7 l7proto httpvideo 
RETURN     0    --  anywhere             anywhere            LAYER7 l7proto pop3 
RETURN     0    --  anywhere             anywhere            LAYER7 l7proto smtp 

Chain triggers (1 references)
target     prot opt source               destination         
TRIGGER    tcp  --  anywhere             anywhere            tcp dpt:2121 TRIGGER type:out tcp match:2121 relate:49152-65534 
TRIGGER    udp  --  anywhere             anywhere            udp dpt:2121 TRIGGER type:out udp match:2121 relate:49152-65534 

Chain upnp (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             Olga1               tcp dpt:18780 
ACCEPT     udp  --  anywhere             Romina1             udp dpt:60886 
ACCEPT     tcp  --  anywhere             Romina1             tcp dpt:49423 

Chain wanin (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 udp 
TRIGGER    0    --  anywhere             anywhere            TRIGGER type:in match:0 relate:0 
ACCEPT     tcp  --  anywhere             thomas-desktop      tcp dpts:54898:54912 
ACCEPT     udp  --  anywhere             thomas-desktop      udp dpts:54898:54912 

Chain wanout (1 references)
target     prot opt source               destination         
triggers   0    --  anywhere             anywhere            


```

Although i made the iptables --flush I'm not quiet sure whether there can sill be a problem with my PC.  Don't get scarred now but i just now how to create chains but not how to delete ;) so look at that mess :oops: :

```

thomas@thomas-desktop:~$ sudo iptables --list
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  192.168.132.1        192.168.132.255     
ACCEPT     0    --  192.168.26.1         192.168.26.255      
ACCEPT     0    --  thomas-desktop       192.168.1.255       
logaborted  tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED tcp flags:RST/RST 
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
nicfilt    0    --  anywhere             anywhere            
srcfilt    0    --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
srcfilt    0    --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
s1         0    --  anywhere             anywhere            

Chain f0to1 (7 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:6881:6889 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:3900:3999 state NEW 
logdrop    0    --  anywhere             anywhere            

Chain f1to0 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:pop3 state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp spts:1024:5999 dpt:time 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:time state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpts:6881:6889 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:mmcc state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:telnet state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpts:5000:5001 state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp spts:1024:5999 dpt:5000 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:pop3s state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:ftp state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpts:6660:6669 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:6969 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:www state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:webcache state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8008 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8000 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8888 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:https state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:smtp state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:aol 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:1024:65535 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:msnp state NEW 
logdrop    0    --  anywhere             anywhere            

Chain logaborted (1 references)
target     prot opt source               destination         
logaborted2  0    --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        0    --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 

Chain logaborted2 (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `ABORTED ' 
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain logdrop (4 references)
target     prot opt source               destination         
logdrop2   0    --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        0    --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 
DROP       0    --  anywhere             anywhere            

Chain logdrop2 (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `DROPPED ' 
DROP       0    --  anywhere             anywhere            

Chain logreject (0 references)
target     prot opt source               destination         
logreject2  0    --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        0    --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable 
DROP       0    --  anywhere             anywhere            

Chain logreject2 (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `REJECTED ' 
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable 
DROP       0    --  anywhere             anywhere            

Chain nicfilt (1 references)
target     prot opt source               destination         
RETURN     0    --  anywhere             anywhere            
RETURN     0    --  anywhere             anywhere            
RETURN     0    --  anywhere             anywhere            
RETURN     0    --  anywhere             anywhere            
RETURN     0    --  anywhere             anywhere            
RETURN     0    --  anywhere             anywhere            
RETURN     0    --  anywhere             anywhere            
logdrop    0    --  anywhere             anywhere            

Chain s0 (1 references)
target     prot opt source               destination         
f0to1      0    --  anywhere             localhost           
f0to1      0    --  anywhere             192.168.132.1       
f0to1      0    --  anywhere             192.168.132.255     
f0to1      0    --  anywhere             192.168.26.1        
f0to1      0    --  anywhere             192.168.26.255      
f0to1      0    --  anywhere             thomas-desktop      
f0to1      0    --  anywhere             192.168.1.255       
logdrop    0    --  anywhere             anywhere            

Chain s1 (1 references)
target     prot opt source               destination         
f1to0      0    --  anywhere             anywhere            

Chain srcfilt (2 references)
target     prot opt source               destination         
s0         0    --  anywhere             anywhere          

```

looking at that once again i'm quiet sure that i will not update to hardy but make a new fresh install. That's the good thing about linux. Every now and then is a new version coming so you don't have to get nervous if you messed up lot's of configurations - with the next version you get a new chance...

Anyway it would be nice if i could use bittorrent on a normal speed. And it would be nice if someone could tell me how to delete chains ;)

Thanks!

Thomas

---

### Post by hyper_ch on 2008-03-18
did you enable UPnP on the router?

---

### Post by njparton on 2008-03-18
In your new router, forward those ports to your computer.

---

### Post by thomas7.10 on 2008-03-18
In the router the UPnP is activated and i can even see active UPnP connections. But not from my machine. The mshine it is working with is a windows.

The ports are forwarded to my computer but it still doesn't seem to work,

Thomas

---

### Post by hyper_ch on 2008-03-18
if the router has UPnP activated then I think it is the firewall on your computer that prevents the connections...

---

### Post by thomas7.10 on 2008-03-18
yes but i flushed the iptables on my computer...

---

### Post by hyper_ch on 2008-03-18
well, all I can say is that if UPnP is activated on the router you normally shouldn't have port forwarding issues and as you say there are connections on the router... the conclusion is that it's your computer no accepting those.

Download kTorrent, go the the plugins there and activate UPnP and then check with a well-seeded torrent file whether this works.

---

### Post by philinux on 2008-03-18
I'd give Deluge a whirl. It seems to work out the box without any fiddling with routers or iptables.

---

### Post by thomas7.10 on 2008-03-18
Ok the ktorrent says as well that there is no incomming connection and that it might be firewalled.

So but how can that be?

Is there a possiblitity to really delete everything from the iptables and start again from the beginning?

In my first post you can see all the things in my iptables and i really want to get rid of them.

-- 
edit:
I do have deluge - was the program that told me that there is no incomming connection and qtorrent as well.

I also flashed my router with another firmware now - DD-WRT is the one i'm using now.

---

### Post by thomas7.10 on 2008-03-18
I try desperately to get rid of all the settings i have in my iptables.

My iptables are still looking like that:

```

thomas@thomas-desktop:~$ sudo iptables --list
[sudo] password for thomas:
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  192.168.132.1        192.168.132.255     
ACCEPT     0    --  192.168.26.1         192.168.26.255      
ACCEPT     0    --  thomas-desktop.skycom.se  192.168.1.255       
logaborted  tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED tcp flags:RST/RST 
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
nicfilt    0    --  anywhere             anywhere            
srcfilt    0    --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
srcfilt    0    --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
s1         0    --  anywhere             anywhere            

Chain f0to1 (7 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:6881:6889 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:3900:3999 state NEW 
logdrop    0    --  anywhere             anywhere            

Chain f1to0 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:pop3 state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp spts:1024:5999 dpt:time 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:time state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpts:6881:6889 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:mmcc state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:telnet state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpts:5000:5001 state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp spts:1024:5999 dpt:5000 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:pop3s state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:ftp state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpts:6660:6669 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:6969 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:www state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:webcache state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8008 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8000 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:8888 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:https state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:smtp state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:aol 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:1024:65535 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:5999 dpt:msnp state NEW 
logdrop    0    --  anywhere             anywhere            

Chain logaborted (1 references)
target     prot opt source               destination         
logaborted2  0    --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        0    --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 

Chain logaborted2 (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `ABORTED ' 
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain logdrop (4 references)
target     prot opt source               destination         
logdrop2   0    --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        0    --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 
DROP       0    --  anywhere             anywhere            

Chain logdrop2 (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `DROPPED ' 
DROP       0    --  anywhere             anywhere            

Chain logreject (0 references)
target     prot opt source               destination         
logreject2  0    --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        0    --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable 
DROP       0    --  anywhere             anywhere            

Chain logreject2 (1 references)
target     prot opt source               destination         
LOG        0    --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `REJECTED ' 
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable 
DROP       0    --  anywhere             anywhere            

Chain nicfilt (1 references)
target     prot opt source               destination         
RETURN     0    --  anywhere             anywhere            
RETURN     0    --  anywhere             anywhere            
RETURN     0    --  anywhere             anywhere            
RETURN     0    --  anywhere             anywhere            
RETURN     0    --  anywhere             anywhere            
RETURN     0    --  anywhere             anywhere            
RETURN     0    --  anywhere             anywhere            
logdrop    0    --  anywhere             anywhere            

Chain s0 (1 references)
target     prot opt source               destination         
f0to1      0    --  anywhere             localhost           
f0to1      0    --  anywhere             192.168.132.1       
f0to1      0    --  anywhere             192.168.132.255     
f0to1      0    --  anywhere             192.168.26.1        
f0to1      0    --  anywhere             192.168.26.255      
f0to1      0    --  anywhere             thomas-desktop.skycom.se 
f0to1      0    --  anywhere             192.168.1.255       
logdrop    0    --  anywhere             anywhere            

Chain s1 (1 references)
target     prot opt source               destination         
f1to0      0    --  anywhere             anywhere            

Chain srcfilt (2 references)
target     prot opt source               destination         
s0         0    --  anywhere             anywhere  

```

I tried already "sudo iptables --flush" and "sudo iptables -t s1 -X"  and "sudo iptables -t s1 -X".

flush seems to work even if it doesn't cause any effect.

"sudo iptables -t s1 -X" and "sudo iptables -t s1 -X" give me that reply:
```

thomas@thomas-desktop:~$ sudo iptables -t s1 -X
iptables v1.3.6: can't initialize iptables table `s1': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
thomas@thomas-desktop:~$ sudo iptables -t s1 -F
iptables v1.3.6: can't initialize iptables table `s1': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

```

I have no clue what to do...

---

### Post by hyper_ch on 2008-03-18
maybe this helps:  [http://gentoo-wiki.com/HOWTO_Setup_UPnP_with_IPTables](http://gentoo-wiki.com/HOWTO_Setup_UPnP_with_IPTables)

---

### Post by thomas7.10 on 2008-03-18
well everything got even more mysterious: When i flush it the iptables are clean but then i can't connect to the internet. So i do wlan0 down and wlan0 up and then the internet works again but all the stuff in the iptables appeared again as well. Isn't there something easy just like: No matter what kind of traffic it is just let it pas?

Can we maybe move my thread to the network forum? Even if i am a absolute beginner i assume my problem is not.

---

### Post by thomas7.10 on 2008-03-18
So now i found kind of a solution. I installed firestarter again and when i start firetarter and klick there on "stop firewall" then i get incomming connections but i'm not that happy with that solution - starting a GUI firewall to stop a firewall...

---

### Post by hyper_ch on 2008-03-18
firestarter is no firewall

---

### Post by thomas7.10 on 2008-03-19
Ok now almost everything is broken...

I deletet firestarter manually searching for firestarter and using root rights. Then i flushed DNSmasq as well because i was setting there something to get my router to work. It seemed to work perfectly fine but then i got lot's of package lost and i can't get anything to work.

Now i'm using the Internet via a win 2000 on a vmware with my mobile phone that supports 3G.

I hope someone can help me with that i get desperated...

---

