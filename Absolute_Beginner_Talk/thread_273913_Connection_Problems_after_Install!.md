---
title: "Connection Problems after Install!"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by Ixnay on 2006-10-09
Hi,

I can't seem to get a connection or access the internet after having installed Ubuntu on my PC (with Windows). I wouldn't really care if I could access the internet on Windows, but I can't. I can't get on to the web, nothing. 

When I go under network settings and look at the connections, all I get is this:

   Modem Connection
   The interface ppp0 is not configured

So I typed pppconfig into the Terminal thingy and it says I have to be root. I don't know what this means.

I've looked around google for similar problems and saw that ifconfig would give some usefull info. (well not to me since I don't understand it) Here's what it said:

lo   Link encap:Local Loopback
     inet addr:127.0.0.1 Mask:225.0.0.0
     inet6 addr: ::1/128 Scope:Host
     UP LOOPBACK RUNNING MTU:16436 Metric:1
     RX Packets:95 errors:0 dropped:0 overruns:0 frame:0
     TX Packets:95 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueue:0
     RX bytes:7260(7.0 KiB) TX bytes:7260(7.0 KiB)

I hope this info helps in solving the problem.
Please help me ](*,) :-D 

Regards,
Chris

---

### Post by Bartender on 2006-10-09
Ixnay -
More info please.  Are we talking dial-up?  Or are we talking cable, or DSL, or Fiber optic?  If dial-up, do you have an internal Winmodem?

From what I understand of Linux networking stuff, the local loopback can be ignored.  I think it's basically your PC talking to itself.  You want to see a second networking device.

There are about a million threads regarding all the fun folks have had with the average internal modem.

---

### Post by HereInOz on 2006-10-09
If you are using a DSL modem/router, or any form of router that offers DHCP services, try setting your IP address in System > Administration > Networking as a static address, enter your Gateway address - the address of the router - and the DNS server addresses of your ISP.  This will often get you up and running.

If you are not using a router or router/modem, please ignore all of the above.

---

### Post by Ixnay on 2006-10-09
We have DSL and a router in the basement...connecting all the 5 PCs in the house...all the other ones are doing fine as far as the internet access goes...

where would I find my IP address?...is it the one listed in the 
ifconfig? (inet addr)

all I see under connections in the admins Networking window is nothing...

---

