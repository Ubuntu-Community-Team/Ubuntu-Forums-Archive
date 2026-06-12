---
title: "Please help me connect to the internet."
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by p_p on 2006-07-15
I am completely new to this and trying to figure things out as I go.  I installed ubuntu 6.06 on my new pc after finally figuring out how to burn an iso.  Now I am trying to get connected to the internet so I can abandon this windows pc.  I am using an actiontec GT701-WG dsl modem which i recently discovered also acts as a router.  This pc (windows) is connected via USB and i'm trying to connect my new pc with ubuntu via ethernet.  I've tried opening a terminal and using "sudo pppeoconf" but i get the response "access concentrator did not respond".  I can ping the ip of the windows pc but if i try to ping [www.google.com](www.google.com) it says "cannot connect to network".  I'm in transition from being a stupid windows user and I could really use a hint.

---

### Post by slider on 2006-07-15
Basically if your router is configured for NAT and DHCP, Ubuntu should pretty much work out of the box. I looked on the web and your router supports both, although it looks like it requires a windows tool to configure it. So:

1. Check that your router has NAT and DHCP enabled.
2. Make sure that Ubuntu is set up to use DHCP for your ethernet connection by going to System -> Administration -> Networking .

If you've done both of these and things still don't work, try this.

Google's IP is 72.14.207.99 . Try pinging that. If it works then there is a problem with your DNS servers. You may have to manually configure them as either your router or the DHCP server isn't providing them for you. If you can't ping external IP's but you can ping the Windows maching, then it seems that it is a router configuration issue and has nothing to do with Ubuntu.

If none of this helps then post the output of "ifconfig" . To be honest I haven't configured dhcp manually on a linux box. Things just worked for me with the steps 1 & 2 above.

---

### Post by Skia_42 on 2006-07-15
So your DSL modem is acting as a Router and you are trying to connect to the internet via ethernet? It sounds like you have the same configuration as me. I had to set up a loopback interface to get internet working. My /etc/network/interfaces file looks like this:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

iface eth0 inet dhcp

iface eth1 inet static
address 129.72.64.183
netmask 255.255.255.0
gateway 129.72.64.183

auto eth1

Make sure to backup the interfaces file if you plan to make any changes to it.

---

### Post by p_p on 2006-07-16
I was unable to ping Google's IP.  How do I manually configure DNS servers?  I see the DNS tab in the networking window but I don't know what to put there.  Here is the result of "ifconfig":


eth0     Link encap: Ethernet   HWaddr   00:E0:18:E7:FF:7A
         UP BROADCAST MULTICAST   MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
         Interrupt:193  Base Address:0x8000

eth1     Link encap: Ethernet   HWaddr   00:0A:5E:09:73:40
         inet6 addr:  fe80: :20a:5eff:fe09:7340/64  Scope:Link
         UP BROADCAST MULTICAST   MTU:1500  Metric:1
         RX packets:124 errors:0 dropped:0 overruns:0 frame:0
         TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:34159 (33.3 KiB)  TX bytes:23770 (23.2 KiB)
         Interrupt:185  Base address:0xa000

lo       Link encap: Local Loopback
         inet addr:127.0.0.1  Mask: 255.0.0.0
         inet6 addr: :1/128  Scope:Host
         UP LOOPBACK RUNNING MTU:16436 Metric:1
         RX packets:165 errors:0 dropped:0 overruns:0 frame:0
         TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:12876 (12.5 KiB)  TX bytes:12876 (12.5 KiB)

Also, how do I set up a loopback interfaces file?

---

### Post by p_p on 2006-07-16
*bump*

Can anyone just tell me how to set up a loopback interface so I can give that a try?  I opened up "network tools" but the "configure" button corresponding to the "loopback" thing is greyed out and unclickable.  I don't know what "etc/network/interfaces" means or how to find that.

---

### Post by confused57 on 2006-07-16
> **p_p said:**
> *bump*

Can anyone just tell me how to set up a loopback interface so I can give that a try?  I opened up "network tools" but the "configure" button corresponding to the "loopback" thing is greyed out and unclickable.  I don't know what "etc/network/interfaces" means or how to find that.

Open a terminal:  Applications---Accessories---Terminal
Then enter:
```
cat /etc/network/interfaces
```
Compare what you have to what Skia_42 has.

The above command just displays the contents of the file, to edit the file you need to use the text editor "gedit".

First, backup the file:
```
sudo cp /etc/network/interfaces /etc/network/interfaces_backup
```

Then to edit the file:
```
gksudo gedit /etc/network/interfaces
```

If something goes wrong after editing, restore the backup:
```
sudo cp /etc/network/interfaces_backup /etc/network/interfaces
```

My cable network connection worked out of the box, so I actually haven't had to edit the file.  Just wanted to give you some Linux basics, feel free to wait until one of the previous posters replies.

---

### Post by slider on 2006-07-17
> **p_p said:**
> I was unable to ping Google's IP.  How do I manually configure DNS servers?  I see the DNS tab in the networking window but I don't know what to put there.  Here is the result of "ifconfig":

...

Also, how do I set up a loopback interfaces file?

If you cannot ping the IP address it is not a DNS issue (or not only a DNS issue) as that is only used to lookup the ip address to match a name.

If you look at the results of ifconfig, you'll notice that you have no IP address. In my experience this means that either you don't have Ubuntu configured to use dhcp or your router is not supplying you with an IP address. I've never manually edited the interfaces file so I have no advice on manually configuring a loopback interace. For comparison here is the output of ifconfig on my system. Notice that you are missing the second line.

```

eth0      Link encap:Ethernet  HWaddr 00:07:E9:71:3A:DC
          inet addr:192.168.1.152  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe71:3adc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:192968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:207264270 (197.6 MiB)  TX bytes:10022970 (9.5 MiB)
          Base address:0xac00 Memory:ff800000-ff820000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:832 (832.0 b)  TX bytes:832 (832.0 b)

```

So when you look at the properties of the network connection under System->Administration->Networking, is it set to use DHCP? If it is then the next step is to read the manual on your modem/router and make sure it is set up as a DHCP server. Can't help you there.

---

### Post by p_p on 2006-07-17
I tried editing the /etc/network/interfaces to include that static IP bit and it didn't help.  I checked the router and it has both DHCP and NAT enabled.  In the "DHCP Users List" it only shows the one pc.  Under "LAN Settings" it shows packets being sent and received via both USB and ethernet.  What now?

---

### Post by Skia_42 on 2006-07-17
Did you backup your original file and replace your /etc/network/interfaces with mine? If it doesn't work you can always go back to the original file. To edit it I would use: > sudo gedit /etc/network/interfaces
This command opens the file "/etc/network/interfaces" with the gedit text editor as root.

---

### Post by p_p on 2006-07-17
> **Skia_42 said:**
> Did you backup your original file and replace your /etc/network/interfaces with mine? If it doesn't work you can always go back to the original file. To edit it I would use: 
This command opens the file "/etc/network/interfaces" with the gedit text editor as root.

Yes, I did go back to the original.  Strangely enough, the original file states that it was provided by the dsl-provider.

---

### Post by Skia_42 on 2006-07-17
Thats odd. So my /etc/network/interfaces file didn't work for you?

---

### Post by p_p on 2006-07-19
The loopback interface didn't work.  I'm still trying to figure out what to do.  This is very frustrating.  I tried entering "dhclient" in the terminal and I got some "permission denied" messages.  Is there any other way to get the modem to give my pc an IP?  I've tried reinstalling Ubuntu and resetting the modem.  Might I have better luck with another distro or another version of Ubuntu?  I installed from the live desktop cd.

---

### Post by p_p on 2006-07-19
Could this have anything to do with the fact that my isp is msn?  I'm about ready to give up.

---

### Post by Skia_42 on 2006-07-19
Don't give up, I know how aggravating it is when things aren't working. It took me a week to get the graphic interface working and another to get internet. Just be patient and you will get the problem solved.

---

### Post by p_p on 2006-07-19
I can't ping the windows machine anymore and I can't get to the router from firefox.  Any suggestions at all are welcome, because I have no idea what to try next.

---

