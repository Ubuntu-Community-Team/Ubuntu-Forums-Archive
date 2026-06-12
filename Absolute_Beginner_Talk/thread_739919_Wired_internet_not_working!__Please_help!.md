---
title: "Wired internet not working!  Please help!"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by anotherghost on 2008-03-30
Hi guys,

I tried looking in other threads about wired internet, but I couldn't solve my problem!  I just installed ubuntu on my new eee pc 4gb, and it's my first linux.  Everything went pretty well, except now that it's all done it doesn't want to connect to the internet through a wired connection.  I don't have a router or anything, it's just going directly into the cable modem, so I really have no idea what to do.

So I looked in the other threads and people usually ask for the ifconfig, so I'll go ahead and post that:
> 
eth0      Link encap:Ethernet  HWaddr 00:1E:8C:B7:A1:7D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:fbfc0000-fc000000 

eth0:avah Link encap:Ethernet  HWaddr 00:1E:8C:B7:A1:7D  
          inet addr:169.254.8.81  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1296 (1.2 KB)  TX bytes:1296 (1.2 KB)



Can anyone help this poor novice out?

---

### Post by bumanie on 2008-03-30
Are you using gutsy gibbon? If so, there has been an issue for many users with the ipv6 stack. This fixes most, but not all internet connection problems in gutsy (it seems to be solved in 8.04).
open firefox, type in the address bar about:config
in the filter, type ipv6. Right click on the text that appears and then left click toggle to change the value to true.
Log out and back in and see if firefox works. If not you can reverse, by going through the same procedure and changing the value back to false.

---

### Post by The Cog on 2008-03-30
I don't know about the eee particularly, but you must look for the word RUNNING in the eth0 status. The ifconfig above is missng the word RUNNING, which would normally indicate that the ethernet cable is not plugged in.

---

### Post by bapoumba on 2008-03-30
Could you please post your** /etc/network/interfaces** ?

---

### Post by louieb on 2008-03-30
Lets see if you can get an IP address from your modem.
open Application>Accessories>terminal and run
```
sudo dhclient
```and hope to see something like this  that meant it was successful:
```
DHCPACK from 192.168.1.1
bound to 192.168.1.7 -- renewal in 940592653 seconds.
```If not then posting the output here would be helpful.

---

### Post by jamesrfla on 2008-03-30
It always seams to be a problem when you have a computer connected right to the modem. I would try manually configuring the IP address. I would also try rebooting the modem.

---

### Post by anotherghost on 2008-03-30
I tried bumanie's tip and there was no change, so I set it back to false.

> **The Cog said:**
> I don't know about the eee particularly, but you must look for the word RUNNING in the eth0 status. The ifconfig above is missng the word RUNNING, which would normally indicate that the ethernet cable is not plugged in.

Yeah that does seem to be a problem - I do have it plugged in though!

> **bapoumba said:**
> Could you please post your** /etc/network/interfaces** ?

I hope I did this right.  It says:
```
auto lo
iface lo inet loopback
```

Alright, and finally, the sudo dhclient:

```
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1e:8c:b7:a1:7d
Sending on   LPF/eth0/00:1e:8c:b7:a1:7d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

---

### Post by bapoumba on 2008-03-30
> **anotherghost said:**
> 

I hope I did this right.  It says:
```
auto lo
iface lo inet loopback
```

Are you using DHCP?

If yes, edit the file:
```
sudo nano /etc/network/interfaces
```
nano is a small text editor working from the command line.

Add:
```
iface eth0 inet dhcp
auto eth0

```
<ctrl>o to save the file, <ctrl>x to exit nano

```
sudo /etc/init.d/networking restart
```
to restart the network. Network should be working.

Please post the output to:
```
ifconfig
```

---

### Post by anotherghost on 2008-03-30
Well I'm sad to say that I'm not sure whether I'm using DHCP because I'm not sure what it is (sorry, said I was a novice :P).  I went ahead and did what you said anyway though (you meant to add that code, right?  not replace the existing with it?).  So now my /etc/network/interfaces looks like this:
```
auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth0
```

Then I did the other stuff, and here is the ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1E:8C:B7:A1:7D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:fbfc0000-fc000000 

eth0:avah Link encap:Ethernet  HWaddr 00:1E:8C:B7:A1:7D  
          inet addr:169.254.8.81  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Memory:fbfc0000-fc000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)


```

I noticed that after I did this, the explanation point disappeared from the network configuration icon.  When I click on it now there's a check by wired connection, but the internet still doesn't work when I try to pull up google in firefox.  The greyed out 'wired connection' also disappeared from the dropdown network menu, leaving me with only manual configuration.

---

### Post by The Cog on 2008-03-30
You can do all the configuration you like. If ifconfig doesn't say RUNNING then you will not be able to use the wired interface. You won't be able to send or receive packets so DHCP and all the other stuff won't work. Concentrate on getting the interface RUNNING and once that is done, then you can worry about the configuration.

I know someone who installed Ubuntu on his eee and I don't remember him saying he had problems with his wired connection. But I can't contact him at the moment to check I'm afraid.

Did the wired connection work before you installed Ubuntu? Did you test it? I wonder if hte cable or the hardware might be the issue.

---

### Post by anotherghost on 2008-03-30
Honestly I don't know whether it worked before I switched OS, I never tried it.  The reason I'm trying now is because I don't have the wireless working on it yet and I need to download some kind of thing for that according to the guide I used to install Ubuntu.

[http://www.sampletheweb.com/2007/12/09/ubuntu-on-the-asus-eee-pc-part-1-or-how-to-run-a-functional-ubuntu-install-off-a-usb-drive/]("http://www.sampletheweb.com/2007/12/09/ubuntu-on-the-asus-eee-pc-part-1-or-how-to-run-a-functional-ubuntu-install-off-a-usb-drive/") (There's the link to that, if that helps at all)

How do I get it to say RUNNING?  Is there something else that could have gone wrong other than just my ethernet port not working?  Like the driver for the port didn't get installed or something?

---

### Post by bapoumba on 2008-03-30
Yes, you had to keep the lo loopback, and add the info for eth0. 
At least, eth0 is seen and should be working.

Please post the output to:
```
ping google.com
ping 64.233.187.99
```

Did you set up DNS?
```
cat /etc/resolv.conf
```
With DHCP, you do not need to set the nameservers, but meh..

One more thing, you may have to use a static IP, I know how to set that up in the interfaces file, but do not know how to find out if this is really the case here. Anyone?

Edit: disregard this post, follow TheCog's one.

---

### Post by anotherghost on 2008-03-30
Well when I pinged google, it said it was an unknown host.  When I pinged that IP, it gave me:
```
From 169.254.8.81 icmp_seq=1 Destination Host Unreachable
```
and kept pinging and saying that.

Also, I tried to cat /etc/resolv.conf and it gave me a no such file or directory.  I looked in /etc/ and it certainly didn't seem to be there.

---

### Post by bapoumba on 2008-03-30
> **The Cog said:**
> You can do all the configuration you like. If ifconfig doesn't say RUNNING then you will not be able to use the wired interface. You won't be able to send or receive packets so DHCP and all the other stuff won't work. Concentrate on getting the interface RUNNING and once that is done, then you can worry about the configuration.

I know someone who installed Ubuntu on his eee and I don't remember him saying he had problems with his wired connection. But I can't contact him at the moment to check I'm afraid.

Did the wired connection work before you installed Ubuntu? Did you test it? I wonder if hte cable or the hardware might be the issue.

> **anotherghost said:**
> Well when I pinged google, it said it was an unknown host.  When I pinged that IP, it gave me:
```
From 169.254.8.81 icmp_seq=1 Destination Host Unreachable
```
and kept pinging and saying that.

Also, I tried to cat /etc/resolv.conf and it gave me a no such file or directory.  I looked in /etc/ and it certainly didn't seem to be there.
I've edited my previous post, I had not seen The Cog's one coming in.
So please answer The Cog's question and follow their advices :)

Found this, making me thing it should work:
[http://wiki.eeeuser.com/debian:eeeos:home]("http://wiki.eeeuser.com/debian:eeeos:home")
Did you run **sudo dhclient **as recommended in the above link?

Also here: [https://help.ubuntu.com/community/EeePC]("https://help.ubuntu.com/community/EeePC"), there are infos under the ethernet section.

---

### Post by anotherghost on 2008-03-30
Eureka!!

That last link did it for me - I don't know why, but removing the battery and restarting everything worked!  The ethernet is working now, I just loaded google.  Awesome!  Thank you so much.

---

### Post by bapoumba on 2008-03-30
Glad to see you got it to work! Congratulations :)

---

### Post by The Cog on 2008-03-30
Excellent! Good link, bapoumba.

> How do I get it to say RUNNING?
RUNNING indicates it's working. Plugging the cable in makes it RUNNING (normally). It's like having the green light on. It seems not to be a very well known thing to look for though.

---

### Post by rkrakora on 2008-04-01
I have the identical message as the thread originator experienced:

No DHCPOFFERS received
No working leases in persistent database - sleeping.

Any other suggestions?

Rich

EDIT:  brought laptop home, tried reinstalling Xubuntu [text], unplugged network card, plugged in card.  Amazingly I have network access.  I think I have an issue with the router at work?  Issue resolved?

---

