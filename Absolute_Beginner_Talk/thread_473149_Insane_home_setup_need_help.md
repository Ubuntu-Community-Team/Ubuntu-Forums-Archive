---
title: "Insane home setup need help"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by kyrhash on 2007-06-13
Ok I have a linksys cable modem hoked up to a D-link DI 524 router which is where i get my internet connection.  This is all in my "computer room", i know that this all works because i can get on my XP computer in the computer room.  I use these things=([http://www.netgear.com/Products/PowerlineNetworking/PowerlineEthernetAdapters/XE102G.aspx](http://www.netgear.com/Products/PowerlineNetworking/PowerlineEthernetAdapters/XE102G.aspx), sorry couldn't get the link to work) to broadcast the signal into my room (across the house).  My new machine in my room runs ubuntu and it refuses to get internet access.  

The ifconfig command yeilds this:

eth0      Link encap:Ethernet  HWaddr 00:16:17:EF:D4:D7  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:10376 (10.1 KiB)
          Interrupt:21 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:16:17:EF:D4:D7  
          inet addr:169.254.10.149  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12108 (11.8 KiB)  TX bytes:12108 (11.8 KiB)

---

### Post by kyrhash on 2007-06-13
... anyone

---

### Post by punx45 on 2007-06-13
what is the IP address of your router?

---

### Post by kyrhash on 2007-06-13
192.168.0.1

---

### Post by kyrhash on 2007-06-13
What does the IP address tell you?

---

### Post by nukkariffic on 2007-06-13
I'm thinking at this point Ubuntu is not seeing your wireless adapter.  What kind of adapter are you using?

---

### Post by kyrhash on 2007-06-13
I am using a wired adapter the Netgear things are used to transmit a signal or something to each other so that they can use Ethernet wires.  I don't have a wireless receiver on the computer that i am trying to fix, however my, D-link DI524 is a wireless broadcaster.

---

### Post by BHelts on 2007-06-13
is your room "across the house" on the same circuit breaker?  i think ethernet over power lines need to be on the same circuit.

---

### Post by djchandler on 2007-06-13
> **kyrhash said:**
> I am using a wired adapter the Netgear things are used to transmit a signal or something to each other so that they can use Ethernet wires.  I don't have a wireless receiver on the computer that i am trying to fix, however my, D-link DI524 is a wireless broadcaster.

Is the wireless router also your dhcp server? I don't understand how you are getting the ip address you are getting, unless it is assigned so it will work properly on another lan. Go into your network settings and make sure it is set to be assigned an ip address dynamically by the router, which I presume is also the dhcp server. What are the ip addresses of other computers on the lan? Ubuntu is not seeing the router at all (obviously.)

---

### Post by kyrhash on 2007-06-13
At one point i had my XBOX 360 working with live in that very same room and plug, no major electrical outlets have been changed however i am beginning to think that it may be a problem as my 360 refuses to work on the same connection.  it being the netgear thingy.

---

### Post by djchandler on 2007-06-13
One quick thought. Would it be impossible to use a really long run of  cat 5e cable since the netgear thingy is acting up?

---

### Post by kyrhash on 2007-06-13
nope it is at least 75 feet and the longest wire that i have is 25 ft and i dont have an old wireless card around.

---

### Post by DasClown on 2007-06-13
> **djchandler said:**
> Is the wireless router also your dhcp server? I don't understand how you are getting the ip address you are getting, unless it is assigned so it will work properly on another lan. Go into your network settings and make sure it is set to be assigned an ip address dynamically by the router, which I presume is also the dhcp server. What are the ip addresses of other computers on the lan? Ubuntu is not seeing the router at all (obviously.)

I agree with djchandler.  You should change your ip address and subnet mask to have it on the same subnet.  For example my router ip is 192.168.1.1 with 255.255.255.0 subnet mask and my first hosts (this computer) address is 192.168.1.100 with a subnet mask of 255.255.255.0  and my second host is 192.168.1.101 and so on.  You'll either have to change it statically on your host or enable DHCP on your router.

Hope this helps you. I'm new to Ubuntu myself!:D

---

### Post by kyrhash on 2007-06-13
DHCP is set to on on my router and my Ubuntu computer, how do i change my subnet in feisty?

---

### Post by DasClown on 2007-06-13
Your Ip address is an APIPA address.  Which means either that PC can't find a dhcp or the dhcp in your router failed.  
Anyway if you want to change your Ip address click on "system" at the top of the desktop then click administration.  After that click on "Network".  Which will bring up your network settings.  On MY pc it lists a WIRED CONNECTION so i'm assuming yours would say WIreless connection? Click on that then click properties.  
This will bring up your device settings.  Under configuration mine says "Automatic Configureation (DHCP).  If you click in there a drop window will allow you to change it to static which will allow you to input an ip address, subnet mask and default gateway (Ip address of your router)

---

### Post by nymphaeles on 2007-06-13
the IP address tells me that your didn't get an IP address from a DHCP server, which means connection to the router never established.

To quickly identified whether or not your wireless card is working, use a wired connection and reboot the machine to see if it gets an IP from your router DHCP server.

---

### Post by kyrhash on 2007-06-13
I finally figured out what the problem was, i had been using VMware to test feisty before i installed it.  Turns out the VMware had created a connection just for itself which turned out to be the signal that the netgear thing was trying to transmit.  So i uninstalled vmware and got rid of those connections and boom internet was connected.

---

### Post by djchandler on 2007-06-13
> **DasClown said:**
> Your Ip address is an APIPA address.  Which means either that PC can't find a dhcp or the dhcp in your router failed.  
Anyway if you want to change your Ip address click on "system" at the top of the desktop then click administration.  After that click on "Network".  Which will bring up your network settings.  On MY pc it lists a WIRED CONNECTION so i'm assuming yours would say WIreless connection? Click on that then click properties.  
This will bring up your device settings.  Under configuration mine says "Automatic Configureation (DHCP).  If you click in there a drop window will allow you to change it to static which will allow you to input an ip address, subnet mask and default gateway (Ip address of your router)

I think we are all a little confused. I know I am, but I'll give it a shot.

First Issue as I understand it:
Your XBOX 360 stopped being able to use the Netgear thingy to use your home electrical wiring. This may mean it has failed. You need another method of connecting Ubuntu to your network,  I say if you're going to buy something else anyway, get 75-100 feet of cat 5e cable you will need to run between the router and the ethernet adapter in the Ubuntu box. That would be my preference. Or just carry the Ubuntu box back to where everything else is and use the cable you have to make sure it is working.

Second issue:
There are two subnets with dhcp servers involved, one being the router, the other is your Ubuntu box. I understand you to actually have a wired connector for the network on both the router and your Ubuntu box, because you were using the Netgear thingies before to facilitate the hardwired connection. DasClown is correct as to go about changing the Ubuntu box to accept an IP address from the DHCP server operating within the router, but I believe it will say "wired connection." I'll attach screenshots of what you should be looking at to make the change in Ubuntu to accept a dynamically generated IP address from the router.

[ATTACH]35322[/ATTACH]     [ATTACH]35323[/ATTACH]

Good Luck! :)

---

### Post by djchandler on 2007-06-13
> **kyrhash said:**
> I finally figured out what the problem was, i had been using VMware to test feisty before i installed it.  Turns out the VMware had created a connection just for itself which turned out to be the signal that the netgear thing was trying to transmit.  So i uninstalled vmware and got rid of those connections and boom internet was connected.

Well now we know how you got that odd IP address at least. I hope I remember the VMWare problem for what it is next time we see it. But then maybe I won't have to because you'll help them. Right, kyrhash?

Now I'm insane!

Just Kidding! LOL

:p

---

