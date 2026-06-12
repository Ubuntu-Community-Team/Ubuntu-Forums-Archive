---
title: "I've lost my internet connection"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by Nameless on 2006-01-06
I can't seem to get Ubuntu to connect to the internet.  I have a wired connection that was working at last night, but when I woke up this morning, I was not able to connect to the internet. 

Here's what I've tried so far: 

I reboot and reset my router and that didn't work.  I know the router is connected to the interent b/c I'm connected with a second computer. 

I am not able to ping my router via the terminal, so I think there is something wrong with my connection from my Ubuntu machine to the router. 

I searched the forums and tried the solutions given here that worked (ie adding the acpi commands to my grub boot file): [http://ubuntuforums.org/showthread.php?t=110545](http://ubuntuforums.org/showthread.php?t=110545)

So far I'm at a loss.  I realize to help, someone will need a few outputs so here goes:

```

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:11:95:23:7C:39
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe23:7c39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:130440 (127.3 KiB)  TX bytes:23677 (23.1 KiB)
          Interrupt:11 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2221 (2.1 KiB)  TX bytes:2221 (2.1 KiB)


route -n:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

cat /etc/network/interfaces:
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

```

So, can anyone help me with this one? I can't figure out why it would have just stopped when it was working yesterday.

---

### Post by mips on 2006-01-06
Follow this guide, [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

Start at the top and work your way down each step. At each step please paste your output here.

Why not post in the networking forum ?

---

### Post by Nameless on 2006-01-06
[QUOTE=mips]Follow this guide, [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

Start at the top and work your way down each step. At each step please paste your output here.

Why not post in the networking forum ?[/QUOTE]


I guess I should have probably sent this to the newtwork forums.  I think I just go the the n00b forum by default....

Anyhow, I tried all of the steps on the above link and below is what I had for outputs:

```


sudo mii-tool eth0:
negotiated 100baseTx-FD, link ok


```

So the above looks like the linking is working

```


ifconfig eth0:
eth0      Link encap:Ethernet  HWaddr 00:11:95:23:7C:39
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe23:7c39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:398166 (388.8 KiB)  TX bytes:10197 (9.9 KiB)
          Interrupt:11 Base address:0xdc00


lspci | grep Eth:
0000:02:09.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)


```

The above makes it look like the driver is properly loaded

The ifconfig showed that I had an IP address so I tried pinging my router and below is what I got: 

```


route -n:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

ping 192.168.0.1:
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
41 packets transmitted, 0 received, 100% packet loss, time 39993ms

ping 192.168.0.100:
PING 192.168.0.100 (192.168.0.100) 56(84) bytes of data.
64 bytes from 192.168.0.100: icmp_seq=1 ttl=64 time=0.078 ms
64 bytes from 192.168.0.100: icmp_seq=2 ttl=64 time=0.042 ms
64 bytes from 192.168.0.100: icmp_seq=3 ttl=64 time=0.042 ms
64 bytes from 192.168.0.100: icmp_seq=4 ttl=64 time=0.040 ms
64 bytes from 192.168.0.100: icmp_seq=5 ttl=64 time=0.041 ms
64 bytes from 192.168.0.100: icmp_seq=6 ttl=64 time=0.041 ms

--- 192.168.0.100 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4999ms
rtt min/avg/max/mdev = 0.040/0.047/0.078/0.014 ms


```

So I was able to ping my router if I use 192.168.0.100 but not if I used 192.168.0.1.  The latter is what I use if I want to actually change the router settings, which I'm not able to do from a web browser on my Ubuntu machine.  I am able to using my other computer, however. 

Next I tried pinging an outside website with both numbers and by name and both results were negative:

```


ping 209.98.65.80:
PING 209.98.65.80 (209.98.65.80) 56(84) bytes of data.

--- 209.98.65.80 ping statistics ---
39 packets transmitted, 0 received, 100% packet loss, time 38004ms

ping www.mpr.org:
ping: unknown host www.mpr.org


```

Lastly, here is the output of my resolv.conf file: 

```

search columbus.rr.com
nameserver 192.168.0.1


```


So, I don't know what my next step would be.

---

### Post by mips on 2006-01-06
When you ping 192.168.0.100 you are actaully pinging your own ethernet interface and not the router.

Make sure the ethernet cables are properly seated on bothe side. Also try swapping the cable between the two ports you are using on the router. Swap the cable between the PCs.

What happens when you configure a static IP address, Netmask & gateway ?

Do you have a firewall installed ?

What router do you have, make&model ?

---

### Post by Nameless on 2006-01-06
[QUOTE=mips]
Make sure the ethernet cables are properly seated on bothe side. Also try swapping the cable between the two ports you are using on the router. Swap the cable between the PCs.

What happens when you configure a static IP address, Netmask & gateway ?

Do you have a firewall installed ?

What router do you have, make&model ?[/QUOTE]


I ruled out that it might be an ethernet cable problem by switching the cables on the computers.  Both cables worked on my 2nd computer.  I also switched the ports on the router for my second computer and both were working. 

I do not have a firewall installed.

I'm using a Dlink Router - DI-524 Model.  

I'll have to look into switching to a static IP.  I don't know how to do that, so I'll search around and post back with some results.  The last time I tried to do that was on my windows machine a while back and I was able to set the IP static, but when the ISP changed it I wasn't able to connect again until I set it back to dynamic.  Will I have that same problem here?

---

### Post by Nameless on 2006-01-06
Alright, this is a little strange:  I was tinkering around with the router and I went in and updated the firmware.   I then restarted the router and I had access to the internet on my Ubuntu machine again. 

I can't believe it was that simple and I didn't think to try that a lot sooner.  

Maybe that's the reason I should continue to post in the n00b forum :smile: 

Thanks for your help, mips

---

### Post by mips on 2006-01-07
D-Link is known for this imho. They seem to require v2 firmware for some people in order for everything to work.

Had you told me it was a D-Link it would have been the first thing I suggested.

The good thing is that everything works ;) !

---

