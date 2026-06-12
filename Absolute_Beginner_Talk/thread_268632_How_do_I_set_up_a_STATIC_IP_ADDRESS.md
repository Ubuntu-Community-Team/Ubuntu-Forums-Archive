---
title: "How do I set up a STATIC IP ADDRESS?"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by seamus7 on 2006-09-30
I need to set up a static ip address in order to properly forward my port. Also, how do I open a port? I'm new to Ubuntu (love it) and can't find detailed or clear instructions as to how to do this. Can anyone help?

---

### Post by petri on 2006-09-30
Have you seen the Dapper guide? :) I hope this is an answer [http://ubuntuguide.org/wiki/Dapper#How_to_activate.2Fdeactivate_network_connections](http://ubuntuguide.org/wiki/Dapper#How_to_activate.2Fdeactivate_network_connections)

---

### Post by wpshooter on 2006-09-30
> **seamus7 said:**
> I need to set up a static ip address in order to properly forward my port. I'm new to Ubuntu (love it) and can't find instructions as to how to do this. I've searched but come up with nothing. Can anyone help?

If you are using Dapper Drake, my recommendation would be that you do this.  Hope you can make out this screenshot.  If not write-back and I will give you detailed flow.  This is under **System** - **Administration** - **Networking**

Good luck.

---

### Post by seamus7 on 2006-09-30
Thanks. Yeah. I know how to get to the Networking menu in Ubuntu Dapper and find the Static IP Address configuartion window.

But do you know how I go about determining what the entries ought to be in order to set up a proper static ip address? Where do I find the appropriate figures to plug in there?

Also, how would I go about opening a port?

Thanks for the quick replies by the way! :)

---

### Post by wpshooter on 2006-09-30
I am no expert on networking but I think this may depend on what type of connectivity you have.  First try issuing the **ifconfig** command at the terminal and see if it does not give you this info.

---

### Post by Anonii on 2006-09-30
Thread hijack, but what are the disadvantages of static? Can your ISP charge you more, or something(dsl)? 
:/

---

### Post by seamus7 on 2006-09-30
I would prefer to use KTorrent on my Gnome Desktop in Ubuntu Dapper but I just can't get it to download at full speed and that's the whole point of torrents: fast downloads for large files.

Instead I'm just going back to uTorrent (via Wine) since I've read it all plays nicely together. However uTorrent requires that I forward a port which requires I set up a static ip address. I'm following the directions on PortForward.com for my Speedstream 5200 modem.

I typed ```
ifconfig
``` in a terminal and got the ip and mask address. I typed ```
route
``` in a terminal to get my gateway address (i hope that's what it was).

I'm going to try using those figures for the static ip address window. I have no idea if those are correct or not though. No one who knows how to do this properly seems to visit this part of the forum. :(

---

### Post by NetworkGuy on 2006-09-30
Seamus7,

Before you setup a static IP address, you have to determine what your router uses for it's DHCP pool.  You have to assign yourself an address outside of that pool.  You'll need to check your router instructions for finding that out.

Once you have that information, you can assign yourself a static IP address.  If you need help, please post the results of an ifconfig, route and "cat /etc/resolv.conf" and we should be able to help you get the job done.

---

### Post by jimrz on 2006-09-30
> **seamus7 said:**
> I need to set up a static ip address in order to properly forward my port. Also, how do I open a port? I'm new to Ubuntu (love it) and can't find detailed or clear instructions as to how to do this. Can anyone help?

how are you connecting? wired or wifi? are you using network-manager, which i think still only works with dhcp?

in any event, the easiest solution may be to go into your router and check for an option to reserve a specific address for a specific machine/mac address. this works well for me. it gives stactic ip functionality for my network while still using dhcp, which allows me to continue using network-manager.

---

### Post by oliviacond on 2006-12-02
> **NetworkGuy said:**
> Seamus7,

Before you setup a static IP address, you have to determine what your router uses for it's DHCP pool.  You have to assign yourself an address outside of that pool.  You'll need to check your router instructions for finding that out.

Once you have that information, you can assign yourself a static IP address.  If you need help, please post the results of an ifconfig, route and "cat /etc/resolv.conf" and we should be able to help you get the job done.

This is my result :

> 
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:B5:52:4D  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:feb5:524d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20637 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21687029 (20.6 MiB)  TX bytes:2153463 (2.0 MiB)
          Interrupt:185 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

> 
~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         DD-WRT          0.0.0.0         UG    0      0        0 eth0

> 
~$ cat /etc/resolv.conf
nameserver 192.168.1.1


---

### Post by seamus7 on 2007-07-13
I'm now using a Belkin wireless router. I set it as an Access Point for my Speedstream 5200 DSL Modem-Router. I'm now on Feisty and manually configuring Network Manager to use an internal Static IP. I also now just use Azureus 2.5 (not 3) as my bit torrent client.

---

