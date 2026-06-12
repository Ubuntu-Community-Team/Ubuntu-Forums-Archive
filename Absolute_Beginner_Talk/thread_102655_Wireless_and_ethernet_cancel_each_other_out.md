---
title: "Wireless and ethernet cancel each other out?"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by qiemem on 2005-12-12
I'm in a college dorm where I can connect either via wireless or an ethernet cable. But when they are both active, any attempt to access the internet times out (though it still says I'm sending and receiving packages). However, both cable and wireless work fine when I disable one of them. So its not that big of a deal, but it is kind of obnoxious. Plus, they go in to different networks (or something, I don't know much about networking), so, for instance, having only one or the other limits what I can access via DAAP.
More than anything, its just kinda weird. Any ideas?

---

### Post by cwaldbieser on 2005-12-12
[QUOTE=qiemem]I'm in a college dorm where I can connect either via wireless or an ethernet cable. But when they are both active, any attempt to access the internet times out (though it still says I'm sending and receiving packages). However, both cable and wireless work fine when I disable one of them. So its not that big of a deal, but it is kind of obnoxious. Plus, they go in to different networks (or something, I don't know much about networking), so, for instance, having only one or the other limits what I can access via DAAP.
More than anything, its just kinda weird. Any ideas?[/QUOTE]
You should be able to use both.  It is probably a routing issue.  When you are experiencing the problem type the following commands in the terminal, and then post the output here:
```

$ ifconfig
$ route

```
This will show info about your network cards as well as your current routing table.  My thought is that maybe when both are enabled, your routing table gets messed up, somehow.

---

### Post by qiemem on 2005-12-12
```
bryan@BryanH:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:79:5E:B2
          inet addr:169.254.26.13  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::211:43ff:fe79:5eb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:223522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:87426611 (83.3 MiB)  TX bytes:5516043 (5.2 MiB)
          Interrupt:18

eth1      Link encap:Ethernet  HWaddr 00:12:F0:48:12:71
          inet addr:134.10.121.49  Bcast:134.10.127.255  Mask:255.255.248.0
          inet6 addr: fe80::212:f0ff:fe48:1271/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:122755 errors:0 dropped:155273 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:54345597 (51.8 MiB)  TX bytes:966878 (944.2 KiB)
          Interrupt:17 Memory:dcffd000-dcffdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:780706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:780706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:86291635 (82.2 MiB)  TX bytes:86291635 (82.2 MiB)

bryan@BryanH:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
134.10.120.0    *               255.255.248.0   U     0      0        0 eth1
134.10.16.0     *               255.255.240.0   U     0      0        0 eth0
169.254.0.0     *               255.255.0.0     U     0      0        0 eth0

```

There ya go. Does that help at all?
Thanks!

---

### Post by cwaldbieser on 2005-12-13
[QUOTE=qiemem]```
bryan@BryanH:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:79:5E:B2
          inet addr:169.254.26.13  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::211:43ff:fe79:5eb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:223522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:87426611 (83.3 MiB)  TX bytes:5516043 (5.2 MiB)
          Interrupt:18

eth1      Link encap:Ethernet  HWaddr 00:12:F0:48:12:71
          inet addr:134.10.121.49  Bcast:134.10.127.255  Mask:255.255.248.0
          inet6 addr: fe80::212:f0ff:fe48:1271/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:122755 errors:0 dropped:155273 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:54345597 (51.8 MiB)  TX bytes:966878 (944.2 KiB)
          Interrupt:17 Memory:dcffd000-dcffdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:780706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:780706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:86291635 (82.2 MiB)  TX bytes:86291635 (82.2 MiB)

bryan@BryanH:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
134.10.120.0    *               255.255.248.0   U     0      0        0 eth1
134.10.16.0     *               255.255.240.0   U     0      0        0 eth0
169.254.0.0     *               255.255.0.0     U     0      0        0 eth0

```

There ya go. Does that help at all?
Thanks![/QUOTE]
Yessiree!  Basically, it is like I thought.  You have no default route set up at this point, so when you try to send a packet to the Internet, it will have no idea where to go.

Another odd thing is that it looks like your eth0 card is talking to 2 different subnets, which shouldn't really be possible.

Do you use DHCP or are the IPs set up to be static?  Can you find out the IP addresses of your gateways (routers) for each NIC, and also determine which one you want to use to get to the Internet?  One we have that info, I believe we can set you up properly.

---

### Post by qiemem on 2005-12-13
DHCP, I think, but I'm not sure. Honestly, I know very little about this networking stuff. I don't know what you mean by IP addresses of my gateways for each NIC... Like the range of IP addresses assigned? If so (from whatsmyip.org), NetRange: 134.10.0.0 - 134.10.255.255. Er, my current IP address is 134.10.30.128. Is this the info you're looking for? If not, how can I find out?

Thank you!

---

### Post by cwaldbieser on 2005-12-13
[QUOTE=qiemem]DHCP, I think, but I'm not sure. Honestly, I know very little about this networking stuff. I don't know what you mean by IP addresses of my gateways for each NIC... Like the range of IP addresses assigned? If so (from whatsmyip.org), NetRange: 134.10.0.0 - 134.10.255.255. Er, my current IP address is 134.10.30.128. Is this the info you're looking for? If not, how can I find out?

Thank you![/QUOTE]
Well, since everything works when you have just one connection enabled, you could try posting the results of those same commands when they are working-- the info should be there.  Also, you might want to post the contents of /etc/network/interfaces and etc/dhcp3/dhclient.conf.

---

### Post by qiemem on 2005-12-13
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:79:5E:B2
          inet addr:134.10.30.128  Bcast:134.10.31.255  Mask:255.255.240.0
          inet6 addr: fe80::211:43ff:fe79:5eb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10703901 (10.2 MiB)  TX bytes:307346 (300.1 KiB)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:732026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:732026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:91294808 (87.0 MiB)  TX bytes:91294808 (87.0 MiB)


$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
134.10.16.0     *               255.255.240.0   U     0      0        0 eth0
default         ssr8dorm.reed.e 0.0.0.0         UG    0      0        0 eth0
bryan@BryanH:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid Reednet





auto eth0


$ cat /etc/dhcp3/dhclient.conf
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

```
> Well, since everything works when you have just one connection enabled, you could try posting the results of those same commands when they are working-- the info should be there. Also, you might want to post the contents of /etc/network/interfaces and etc/dhcp3/dhclient.conf.
Here is what I got...

---

### Post by cwaldbieser on 2005-12-13
[QUOTE=qiemem]```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:79:5E:B2
          inet addr:134.10.30.128  Bcast:134.10.31.255  Mask:255.255.240.0
          inet6 addr: fe80::211:43ff:fe79:5eb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10703901 (10.2 MiB)  TX bytes:307346 (300.1 KiB)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:732026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:732026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:91294808 (87.0 MiB)  TX bytes:91294808 (87.0 MiB)


$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
134.10.16.0     *               255.255.240.0   U     0      0        0 eth0
default         ssr8dorm.reed.e 0.0.0.0         UG    0      0        0 eth0
bryan@BryanH:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid Reednet





auto eth0


$ cat /etc/dhcp3/dhclient.conf
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

```

Here is what I got...[/QUOTE]

OK, what I have so far is that one of your cards belongs to a 134.10.16.0/20 network, and it's default gateway is ssr8dorm.reed.e.  We'll need to find out this info for the other interface, too-- I guess I should have been more explicit about that.

The next time you have both interfaces running and you can't seem to get a connection try this command:
```

$ sudo route add -net default gw ssr8dorm.reed.e

```
That should tell any messages you are sending that don't know where to go that they should try to go through the gateway on the 134.10.16.0/20 network-- sorry I keep using the numbers-- I am not sure what these different networks physically correspond to.

I will try to look up how to configure dhcp so it knows you are supposed to use one of your gateways as a default route.

---

### Post by qiemem on 2005-12-14
Oh ya heh sorry:
```

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
134.10.120.0    *               255.255.248.0   U     0      0        0 eth1
169.254.0.0     *               255.255.0.0     U     0      0        0 eth1
default         c120h001.wless. 0.0.0.0         UG    0      0        0 eth1


$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:12:F0:48:12:71
          inet addr:169.254.181.38  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::212:f0ff:fe48:1271/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11009 errors:0 dropped:938682 overruns:0 frame:0
          TX packets:237 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:168145550 (160.3 MiB)  TX bytes:30337869 (28.9 MiB)
          Interrupt:17 Memory:dcffd000-dcffdfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1882650 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1882650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:228391124 (217.8 MiB)  TX bytes:228391124 (217.8 MiB)

```
This is output from when only the wireless is runnging. How do you determine what kind of network it belongs to? 

I also tried what you suggested. Here's what I got (net not working: both connected):
```

$ sudo route add -net default gw ssr8dorm.reed.e

ssr8dorm.reed.e: Host name lookup failure

```

---

### Post by Lambert on 2005-12-14
You get the hostname failure because you can't connect to a nameserver. So it's not able to convert ssr8dorm.... to an ip address

So here's what you need to do.

Connect with just your wired connection and type this command.

host ssr8dorm.reed.e

you should get something like this

ssr8dorm.reed.e has address of x.x.x.x

Note the address then repeat the steps when you're just connected via wireless. but replace ssr8..... with the c120h001.... from your last post. Note that address.

Then go in to this file

sudo gedit /etc/hosts and add these lines to it

ssr8dorm.reed.e x.x.x.x
c120h001.wless. x.x.x.x

where the x.x.x.x equals the address you found

Now this part I'm not knowledgeable about but believe cwaldbieser was on track with.

Run these commands

sudo route add default gw ssr8dorm.reed.e dev eth0
sudo route add default gw c120h001.wless. dev eth1

I believe the dev ethX is important at the end of each command because you want to make sure the routing table for each device is specific.

---

### Post by qiemem on 2005-12-14
Okay, so part  of the problem (with what cwaldbieser was havin me do) is that the gateway is not ssr8dorm.reed.e, its ssr8dorm.reed.edu, it was just cut off when being displayed. Thus, even when I tried host ssr8dorm.reed.e, I got:
```
Host ssr8dorm.reed.e not found: 3(NXDOMAIN)

```
Changed it to .edu, got the ip (oh, but tried adding the correct gateway first, had the same trouble (I think...)) Then I edited the file as Lambert suggested, added the gateway with dev eth0 at the end, and now it works great (well, so far so good).
Same everything with c120h001.wless. 
Really its c127h236.wless.reed.edu. So I did all the proper adjusting, and as far as I can tell, its working.
Thanks for your help everyone!

p.s. just out of curiousity why did I have to set both gateways as defaults. Wasn't the whole point that I wanted the cable to take precedence over the wireless?

---

### Post by cwaldbieser on 2005-12-14
[QUOTE=qiemem]Okay, so part  of the problem (with what cwaldbieser was havin me do) is that the gateway is not ssr8dorm.reed.e, its ssr8dorm.reed.edu, it was just cut off when being displayed. Thus, even when I tried host ssr8dorm.reed.e, I got:
```
Host ssr8dorm.reed.e not found: 3(NXDOMAIN)

```
Changed it to .edu, got the ip (oh, but tried adding the correct gateway first, had the same trouble (I think...)) Then I edited the file as Lambert suggested, added the gateway with dev eth0 at the end, and now it works great (well, so far so good).
Same everything with c120h001.wless. 
Really its c127h236.wless.reed.edu. So I did all the proper adjusting, and as far as I can tell, its working.
Thanks for your help everyone!

p.s. just out of curiousity why did I have to set both gateways as defaults. Wasn't the whole point that I wanted the cable to take precedence over the wireless?[/QUOTE]

Well, my understaning of how the routing table works is that it tries to match the network part of each packet you are sending against an entry in the routing table.  As soon as it finds a match, away it goes!

Since default (which is network 0.0.0.0) matches everything, as soon as it hits that first default entry, it will use that.

The tricky part is that if you turn off that nic, the corresponding routing table entries are also removed.  Since you have a second "default" entry, though, it will pick up the slack.

---

### Post by Lambert on 2005-12-14
> p.s. just out of curiousity why did I have to set both gateways as defaults. Wasn't the whole point that I wanted the cable to take precedence over the wireless? 
Didn't see that in your original post, just you wanted to have two active interfaces. So I guess the question is what is your intentions with having two active interfaces?

You can modify your routing table in many various ways. All internet trafic through wired, just local subnet traffic through wireless. You can balance the two dynamiclaly to increase bandwidth. etc... 

So an example would be

sudo route add -net 169.254.0.0 netmask 255.255.0.0 gw c127h236.wless.reed.edu dev eth1

So all traffic with a destination of 169.254.x.x would go through the wireless route and all other traffic would go through the wired default gateway. (I may be missing something as I'm not 100% understanding routing tables yet but this is the basic idea)

I'm curious now though if you wouldn't mind testing something and posting back. When you have both interfaces active and you set up both default gateways could you run the following command a couple times. What I'd like to see is what path takes precedence or if both are used in a hopping fashion.

tracepath [www.ubuntu.com](www.ubuntu.com)

After a couple lines you can hit ctrl+c

you can use any www. site for this. The first line will be the ip address of your interface and the second line is the router. If you could run this 3 or 4 times and just post back what path was taken ( wired interface or wireless interface or if it alternates) I'd appreciate your post.

---

