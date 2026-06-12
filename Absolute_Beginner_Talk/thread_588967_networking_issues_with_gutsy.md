---
title: "networking issues with gutsy"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Hitchhiker42 on 2007-10-23
I'm really frustrated with this issue, and now I'm having similar problems with two computers and enough to make me tear my hair out because I just want the network to work already!

*takes deep breath*
Networking is not my strong suit, can you tell?

Okay, I have two computers that dual boot Gutsy+Windows on a network with one other Windows computer. All computers can see each other whilst in Windows. All computers can access the Net from any OS.

The first computer (gopher), used to be able to access the network, but when I upgraded to Gutsy, it couldn't anymore. Not sure what's going on here, probably a simple setting I'm overlooking due to my inexperience.

The second computer (beaver), is also upgraded from Feisty, but it has never been able to access the network. To the best of my knowledge, the Samba settings, &c., are identical for both computers.

Any help would be appreciated so much!

---

### Post by NZ-Wanderer on 2007-10-23
Sorry can't help you, but just to let you know you aint alone in this... - I sort of have the same problem as you, all my windows machines have no problems seeing each other, but soon as Gutsy is loaded all windows computers deny all knowledge of it being there (this includes a vmware windows I have inside Gutsy as well)

*** Sits down in corner and gets ready to take notes when the techies arrive *** :) :)

---

### Post by wieman01 on 2007-10-23
Hi, 

Could you tell us a bit more about your hardware & set-up (e.g. Ethernet, wireless), then the network settings (e.g. DHCP or static IP), and what you are trying to achieve. Simply tell us as much as possible. :-)

Which computer should we focus on first?

---

### Post by Hitchhiker42 on 2007-10-23
Ah, sorry... Should've mentioned that in my first post. Both are wired connections, and DHCP. They connect to each other via router, that also facilitates the connection to the internet.

I believe this to be gopher's network card: Realtek RTL-8110SC/8169SC Gigabit Ethernet

beaver's NIC: nVidia CK8S Ethernet Controller

Probably focus on gopher first, as it is my personal computer, so I don't have to kick anyone off to work on it. :)

Any other information y'all need?

---

### Post by wieman01 on 2007-10-23
> **Hitchhiker42 said:**
> Ah, sorry... Should've mentioned that in my first post. Both are wired connections, and DHCP. They connect to each other via router, that also facilitates the connection to the internet.

I believe this to be gopher's network card: Realtek RTL-8110SC/8169SC Gigabit Ethernet

beaver's NIC: nVidia CK8S Ethernet Controller

Probably focus on gopher first, as it is my personal computer, so I don't have to kick anyone off to work on it. :)

Any other information y'all need?
All right, gopher it is then. ;-)

Please run the following for me from a terminal window and post the results if possible (copy the stuff on a USB drive or something):
> route
> route -n
> sudo ifdown -v eth0
> sudo ifup -v eth0
> ifconfig
I assume that "eth0" is your network interface, is that right? Are the computer phyiscally connected to the router?

---

### Post by kthakore on 2007-10-24
I am having a similar problem here is my info

```

kthakore@kthakore:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
kthakore@kthakore:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
kthakore@kthakore:~$ sudo ifdown -v eth0
[sudo] password for kthakore:
Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/wpasupplicant
 route del default gw 192.168.1.1 metric 100 eth0 
ifconfig eth0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
kthakore@kthakore:~$ sudo ifup -v eth0
Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

ifconfig eth0 192.168.1.4 netmask 255.255.255.0                 up
 route add default gw 192.168.1.1 metric 100 eth0 
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant
kthakore@kthakore:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:21:E6:A1:A0:2A  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4221:e6ff:fea1:a02a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6169949 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6413579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:191794452 (182.9 MB)  TX bytes:3883169568 (3.6 GB)
          Interrupt:5 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:354885 (346.5 KB)  TX bytes:354885 (346.5 KB)


```

---

### Post by wieman01 on 2007-10-24
> **kthakore said:**
> I am having a similar problem here is my info
Please... don't hijack other people's threads but open a new one for your specific problem. It will be very tough to help 2 people at a time, plus I don't think that is very polite. 

That said I will of course try to help you if you send me the link to your thread by PM.

---

### Post by Hitchhiker42 on 2007-10-24
> I assume that "eth0" is your network interface, is that right? Are the computer phyiscally connected to the router?
Yes, eth0 is my network interface, and the computers are physically connected to the router via Ethernet cable.

route:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         home            0.0.0.0         UG    0      0        0 eth0


```

route -n

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0

```

 sudo ifdown -v eth0

```

ifdown: interface eth0 not configured

```

sudo ifup -v eth0

```

Ignoring unknown interface eth0=eth0.


```

ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:50:8D:C4:4E:4A  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fec4:4e4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83586467 (79.7 MB)  TX bytes:6441848 (6.1 MB)
          Interrupt:19 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:842157 (822.4 KB)  TX bytes:842157 (822.4 KB)


```

Also, to clarify, as I realized that my first post was rather vaguely worded, both computers can access the internet, it just the home network (file sharing, network printers, &c.) that they can't get at.

---

### Post by drs305 on 2007-10-24
For some reason about the time I upgraded my computers to Gutsy the IP addresses changed. I did a clean install. I had to go into my /etc/HOSTS files and my router and change them to reflect the new IP addresses. Until I did this the other computers could not see them.

---

### Post by wieman01 on 2007-10-24
> **Hitchhiker42 said:**
> Also, to clarify, as I realized that my first post was rather vaguely worded, both computers can access the internet, it just the home network (file sharing, network printers, &c.) that they can't get at.
Ok. 

So you network seems to work. Let's talk about file sharing, etc. then. Is it only between those 2 machines or also sharing with a Windows computer?

I normally use Samba for all sort of sharing. It is not as fast as NFS, but fairly simple in terms of administration.

Now there should be a "Sharing" menu items in "Administration" (not sure what the exact name is, I use KDE, not Gnome). There you can set up sharing of folders, etc. Can you find it?

Once you share a folder, this is how the other computer would access the folder...

1. Open Nautilus
2. Type in:
> smb://192.168.1.**[COLOR="Red"]xxx[/COLOR]**
**[COLOR="Red"]xxx[/COLOR]** being the last token of the client computer's IP address.

That's it. Make sure that the client's username is also registered on the machine that shares the folder. 

I am not sure how clear this is to you, but I'll be around if you have questions.

---

### Post by Hitchhiker42 on 2007-10-28
Right, now I have time to work on the network again, so... (Please forgive my lack of knowledge)

> That's it. Make sure that the client's username is also registered on the machine that shares the folder. 

How do I register it? Do you mean registered with samba, so that it is prompted for a username and password when accessing shared files? I had done that, and it worked okay on gopher (when it was running Feisty), but not on beaver. 


> Is it only between those 2 machines or also sharing with a Windows computer?

It's also sharing with a Windows computer (hedgehog). Hedgehog can see beaver, but not access it, and it used to be able see and access the shared folders on gopher, until I upgraded to Gutsy. When I go to Places>Network on either Gutsy computer, they can see the Windows network, but not the computers on it.

---

