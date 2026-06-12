---
title: "Networking Windows PC's to Ubuntu server"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Amplidude on 2007-07-10
Hi All

I'm headbanging so much the wall has started to bleed. I've set up a Feisty server with 2 NIC cards. One (eth0) goes through a Cisco 800 series router to the internet on a static IP. The other (eth1) through a small Planet hub to a couple of PC's running XP. I'm running DHCP on the internal network, and the firewall through Firestarter. The server connects to the internet, no problem there, but I cannot get the PC's to connect to the network (i.e. no internet or computers present). 

After a struggle I managed to get the driver for eth1 working and the xp machines could see the connection (windows reported them connected) but they still could not connect to the internet. I thought this may be because of the firewall, but after a shutdown the XP machines are no longer connected.

Does the eth1 driver have to be re-loaded after a shutdown? if so, how? And how do I make it persistent?

Assuming the driver does not have to be re-loaded (and even when it was loaded I still could not get the network running) so I have to be missing something somewhere. Not surprising, I'm a newbie.

Please help.


This is the setup:

> tony@Server1:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:B9:0D:D0:B2  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe0d:d0b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2654383 (2.5 MiB)  TX bytes:497494 (485.8 KiB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:4F:63:00:FF:9B  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::24f:63ff:fe00:ff9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11860 (11.5 KiB)  TX bytes:19714 (19.2 KiB)
          Interrupt:16 Base address:0xaf00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14928 (14.5 KiB)  TX bytes:14928 (14.5 KiB)


The IP tables:
> tony@Server1:~$ sudo iptables -L -v
Chain INPUT (policy DROP 2 packets, 666 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  any    any     dnscache1.is.co.za   anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
   81  9370 ACCEPT     udp  --  any    any     dnscache1.is.co.za   anywhere            
    0     0 ACCEPT     tcp  --  any    any     dnscache2.is.co.za   anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
    1    77 ACCEPT     udp  --  any    any     dnscache2.is.co.za   anywhere            
  132 12448 ACCEPT     0    --  lo     any     anywhere             anywhere            
   12   898 ACCEPT     icmp --  any    any     anywhere             anywhere            limit: avg 10/sec burst 5 
    0     0 DROP       0    --  eth0   any     anywhere             255.255.255.255     
   77 13983 DROP       0    --  any    any     anywhere             192.168.1.255       
    0     0 DROP       0    --  any    any     BASE-ADDRESS.MCAST.NET/8  anywhere            
    0     0 DROP       0    --  any    any     anywhere             BASE-ADDRESS.MCAST.NET/8 
    0     0 DROP       0    --  any    any     255.255.255.255      anywhere            
    0     0 DROP       0    --  any    any     anywhere             0.0.0.0             
    0     0 DROP       0    --  any    any     anywhere             anywhere            state INVALID 
    0     0 LSI        0    -f  any    any     anywhere             anywhere            limit: avg 10/min burst 5 
 2858 2589K INBOUND    0    --  eth0   any     anywhere             anywhere            
    0     0 INBOUND    0    --  eth1   any     anywhere             192.168.0.1         
    0     0 INBOUND    0    --  eth1   any     anywhere             192.168.1.2         
  189 23101 INBOUND    0    --  eth1   any     anywhere             192.168.0.255       
    2   666 LOG_FILTER  0    --  any    any     anywhere             anywhere            
    2   666 LOG        0    --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            limit: avg 10/sec burst 5 
    0     0 TCPMSS     tcp  --  any    any     anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
    0     0 OUTBOUND   0    --  eth1   any     anywhere             anywhere            
    0     0 ACCEPT     tcp  --  any    any     anywhere             192.168.0.0/24      state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  any    any     anywhere             192.168.0.0/24      state RELATED,ESTABLISHED 
    0     0 LOG_FILTER  0    --  any    any     anywhere             anywhere            
    0     0 LOG        0    --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  any    any     192.168.1.2          dnscache1.is.co.za  tcp dpt:domain 
  146  9734 ACCEPT     udp  --  any    any     192.168.1.2          dnscache1.is.co.za  udp dpt:domain 
    0     0 ACCEPT     tcp  --  any    any     192.168.1.2          dnscache2.is.co.za  tcp dpt:domain 
   65  4453 ACCEPT     udp  --  any    any     192.168.1.2          dnscache2.is.co.za  udp dpt:domain 
  132 12448 ACCEPT     0    --  any    lo      anywhere             anywhere            
    0     0 DROP       0    --  any    any     BASE-ADDRESS.MCAST.NET/8  anywhere            
  228 16650 DROP       0    --  any    any     anywhere             BASE-ADDRESS.MCAST.NET/8 
    0     0 DROP       0    --  any    any     255.255.255.255      anywhere            
    0     0 DROP       0    --  any    any     anywhere             0.0.0.0             
    0     0 DROP       0    --  any    any     anywhere             anywhere            state INVALID 
 3123  426K OUTBOUND   0    --  any    eth0    anywhere             anywhere            
   80 14089 OUTBOUND   0    --  any    eth1    anywhere             anywhere            
    0     0 LOG_FILTER  0    --  any    any     anywhere             anywhere            
    0     0 LOG        0    --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (4 references)
 pkts bytes target     prot opt in     out     source               destination         
 2858 2589K ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
  189 23101 LSI        0    --  any    any     anywhere             anywhere            

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
  189 23101 LOG_FILTER  0    --  any    any     anywhere             anywhere            
    0     0 LOG        tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
    0     0 LOG        tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
    0     0 LOG        icmp --  any    any     anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       icmp --  any    any     anywhere             anywhere            icmp echo-request 
  189 23101 LOG        0    --  any    any     anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
  189 23101 DROP       0    --  any    any     anywhere             anywhere            

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  0    --  any    any     anywhere             anywhere            
    0     0 LOG        0    --  any    any     anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
    0     0 REJECT     0    --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
 pkts bytes target     prot opt in     out     source               destination         
   13   946 ACCEPT     icmp --  any    any     anywhere             anywhere            
 2856  403K ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
  334 35886 ACCEPT     0    --  any    any     anywhere             anywhere            

The DHCP server:
>  Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"


and the dhpcd.conf file:
> # DHCP configuration generated by Firestarter
ddns-update-style interim;
ignore client-updates;

subnet 192.168.0.0 netmask 255.255.255.0 {
	option routers 192.168.0.1;
	option subnet-mask 255.255.255.0;
	option domain-name-servers Server1;
	option ip-forwarding off;
	range dynamic-bootp 192.168.0.100 192.168.0.254;
	default-lease-time 21600;
	max-lease-time 43200;
}

---

