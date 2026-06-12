---
title: "network problem on ibook G4 NewWorld"
date: 2006-07-28
forum: Apple PPC Users
---

### Post by jayant on 2006-07-28
Hi

I have recently installed Ubuntu 6.06 on my iBook G4 (NewWorld) 14" from a live CD. I am quite happy with it's simple look. However I haven't been able to get on the internet. :( 

I am including the outputs of certain commands that show it is detecting the ethernet controller correctly. I am also getting an IP address. And I am able to ping the local gateway ( 10.0.0.8 ). But I am not able to ping yahoo.com or any other site. I can't get anywhere using firefox either. I am not sure where the problem lies. Is it a firewall problem?

[FONT="Courier New"][SIZE="1"]jayant@killer-ibook-linux:~$ lspci | grep Ethernet
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)

jayant@killer-ibook-linux:~$ lspci -n | grep 20:0f
0002:20:0f.0 0200: 106b:0032 (rev 80)

jayant@killer-ibook-linux:~$ lsmod | grep sungem
sungem                 38948  0
sungem_phy             10432  1 sungem

jayant@killer-ibook-linux:~$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:11:24:44:5D:28  
          inet addr:10.0.0.148  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::211:24ff:fe44:5d28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13698 (13.3 KiB)  TX bytes:24266 (23.6 KiB)
          Interrupt:41 Base address:0xd000[/SIZE][/FONT]

Oh and just to see if the ethernet cable and everything else works, I simply rebooted in to Mac OS X and using the same setup i am able to browse the internet. So i am not sure if it is a firewall problem.

in network-admin, eth0 is active and set to dhcp.

part of /var/log/syslog is attached (don't know if it helps)

Also at every boot I get this message: ( not sure if it is related)
[FONT="Courier New"][SIZE="1"][  17.614094] PCI: Cannot allocate resource region 0 of device 0001:10:18.0
[  17.614113] PCI: Cannot allocate resource region 0 of device 0001:10:19.0[/SIZE][/FONT]

... and the first number always changes.


Any help will be greatly appreciated.

---

### Post by jayant on 2006-07-28
new revelation... it's a dns problem.
i determined that by pinging 64.233.189.104 (google), which worked. so now i just don't know how to fix it. as in my mac os x system preferences it has nothing listed in DNS servers.

i had a look at my linux system again and it seems to me everything is in order but my internet still doesn't work. i can get to google in firefox by using the ip address, but not by typing google.com

also my ifconfig still shows and inet6 addr after i modified the etc/modprobe.d/aliases file to disable ipv6

here's the output of some commands that may be helpful in determining the problem

[SIZE="1"][FONT="Courier New"]jayant@killer-ibook-linux:~$ ping -c 3 64.233.189.104
PING 64.233.189.104 (64.233.189.104) 56(84) bytes of data.
64 bytes from 64.233.189.104: icmp_seq=1 ttl=240 time=333 ms
64 bytes from 64.233.189.104: icmp_seq=2 ttl=240 time=338 ms
64 bytes from 64.233.189.104: icmp_seq=3 ttl=240 time=336 ms

--- 64.233.189.104 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2008ms
rtt min/avg/max/mdev = 333.928/336.025/338.045/1.809 ms

jayant@killer-ibook-linux:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         10.0.0.8        0.0.0.0         UG    0      0        0 eth0

jayant@killer-ibook-linux:~$ cat /etc/resolv.conf
search lan
nameserver 10.0.0.8

jayant@killer-ibook-linux:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface dsl-provider inet ppp
provider dsl-provider

jayant@killer-ibook-linux:~$ cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

jayant@killer-ibook-linux:~$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:11:24:44:5D:28
          inet addr:10.0.0.148  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::211:24ff:fe44:5d28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:45529 (44.4 KiB)  TX bytes:24561 (23.9 KiB)
          Interrupt:41 Base address:0xd000

[/FONT][/SIZE]

please help ! :sad:

---

### Post by rasec on 2006-07-28
It seems like you dhcp server isn't providing you with proper the name server(s) ip addresses. I can think of two ways around this. First way, go under os x and copy down the ip addresses for the name servers. You can do this by going into the terminal program and "cat /etc/resolv.conf". The second way is to get the name server ip addresses from the router directly. After you get the name server ip address add it to your resolv.conf.

If os x is using the same name server as ubuntu, than your firewall might be the problem. I just greped /etc/services and I think that you need ports 42/tcp, 53/tcp, 53/udp open, at least to your lan. Do an "sudo iptables -L to see if you are running a firewall.

---

### Post by jayant on 2006-07-28
i am attaching the services and resolv.conf files from my linux and osx. i tried changing my resolv.conf in linux to match the one in os x. but it didnt help. i changed the line "search lan" to "domain lan". but every time i reboot it goes back to "search lan". in any case it hasnt worked. i am also attaching the output of iptables. 

and in the /etc/services file i added the line 42/udp myself. dont think it is required. does it hurt?

please help!

ps. couldn't attach service.osx.txt as it was too big

---

### Post by rasec on 2006-07-28
Did you do anything to your /etc/hosts file? I just looked at my powerbook's resolv.conf and the only thing that was in it was a single nameserver entry. Try removing the search line in your resolve.conf and restart your network by "sudo /etc/init.d/network restart" and see if that helps.

---

### Post by jayant on 2006-07-28
that didnt work either. :( looks like when i did network restart, it rewrote the resolv.conf file with the search lan line. and yes i changed my hosts file.
before it had the entries as shown in the attached pic

no it has:

```
127.0.0.1 localhost killer-ibook-linux
127.0.1.1 killer-ibook-linux

# The following lines are desirable for IPv6 capable hosts
10.0.0.154 imacg5

```

the imacg5 is just so that i can easily ssh to it and transfer files etc

---

### Post by rasec on 2006-07-28
Are you connecting to an os x server by any chance? I think that they might use Bonjour instead of a traditional dns server, but I'm not sure. One last thing you can try is to set up the connection to use a static ip instead of dynamic. If possible, try to get the name servers that your router is using so that you can bypass the router. Other than that, I'm clueless. You might have better luck resolving this issue by posting in the network forum.

---

### Post by jayant on 2006-07-29
it works now. i'll tell you later how

---

### Post by stmiller on 2006-08-01
I'm having the same problems. I can get an ip address. I can ping yahoo.com, etc. But cannot connect to apt-get update, and firefox spins and times out trying to bring up a webpage. Please tell us what fixed it for you. Thank you!

iBook G4 1 Ghz
Ubuntu 6.06

---

### Post by stmiller on 2006-08-01
Ah, got it (in my case). I was sharing a connection from another OS X machine. The firewall was on, and 'personal web sharing' or something like that must be allowed in the firewall of the routing machine.

---

### Post by raldz on 2006-08-07
if you are having troubles with your DNS, try openning:

/etc/resolv.conf

to open from terminal: sudo gedit /etc/resolv.conf

and try to place this on top of the list:

nameserver 208.67.222.222
nameserver 208.67.220.220


these are name servers provided by [www.opendns.com](www.opendns.com) it also speeds up your browsing a little..

---

### Post by jayant on 2006-08-07
hey raldz
thanks for the reply. i have added the 2 lines. although i managed to get it to work before but hopefully this will make it faster.
thanks
jayant

---

