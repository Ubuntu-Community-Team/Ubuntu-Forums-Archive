---
title: "Having problems connecting to the internet..."
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Rogue Agent on 2007-03-28
I recently installed ubuntu 6.10 on my laptop.  When I first tried to connect to the internet, I just plugged in my ethernet cable and went to the networking part and enabled the connection with auto detect dchp.  It still didn't work.  The network connection icon in the upper right corner toolbar always says that my connection is idle.  I then tried connecting using my wireless pc card.  It is a netgear, w5g11t or something like that.  I think I read somewhere on these forums that it might be plug and go.  That also did not work.  I then read about establishing a pppoe connection.  I have also done that and it has not worked.  I am kind of at a lost of what to do now.  I was thinking it might be my connection at the house, so I am bringing my laptop to work to check it out there.  But if anyone could help me with this, it would be greatly appreciated.  Also my laptop is a Toshiba if that is any help.  It also has this little emblem in the corner that says something like "designed to run with Windows XP," or something close to it.  Could that possibly be the problem?  I was thinking maybe Microsoft just made a deal with Toshiba to have Windows come installed on all their computers and that emblem was just propaganda or whatever.  But thanks in advance to everyone.

---

### Post by eljalill on 2007-03-28
I am very sure, that little emblem is just there to tell you, that the Computer will indeed run under Windows... not that it wont run under any other OS. (Did you ever notice: nearly all non Apple Laptops have that little sticker?)

The problem might as well be the connection in the house, depending on a few things:
What kind of connection do you have? Plug and Play might only work, if you have DSL. If you connect to the internet via an ISDN connection or so, you will most likely have to do more setting up.
Also, the problem could come up, if your connection goes through a proxy. You then have to enable the proxy settings in your browser.
Or you might have to connect via a VPN connection, as e.g often the case with a university network (at least that's where I saw those before).

To find out, as a first step, you could enable the networking via the system panel and then type 
ifconfig into a terminal. In the print out you should see information about your network devices and connections. Do you have an IP? In case you are not sure, post the output here.

---

### Post by shuaibe on 2007-03-28
I also have Toshiba which also have that emblem :)  but I had no problem in connecting to internet via the Ethernet card and the Wireless card using Ubuntu (didn't have to do any settings at all).

Pls goto System->Network Setting and see if your ethernet card and wireless card are listed under the connection tab. Click the activate button for the connection you want to use and try using the internet.

Also on the console type ifconfig to make sure that you are assigned an IP address as told in the above reply! Good luck!

---

### Post by Rogue Agent on 2007-03-28
Thanks guys, I didn't know I would get a response so quickly.  I had to go to the third page to find my post.  Well, I tried connecting at work and still no luck.  Does it make a difference if the connection is DSL or cable?  Because service provider is Comcast and  I think they do cable internet.  As far as running 'ifconfig' in the terminal, this is what popped up:

ath0     Link encap: Ethernet   HWaddr 00:90:96:B7:6D:3F
           inet6 addr:  fe80::290:96ff:feb7:6d3f/64  Scope: Link
           UP BROADCAST RUNNING MULTICAST   MTU: 1500   Metric: 1
           RX packets:0  errors:0  dropped:0  overruns:0  frame:0
           TX packets:0  errors:0  dropped:0  overruns:0  carrier:0
           collisions:0  txqueuelen:0
           RX bytes:0  (0.0 b)   TX bytes:0  (0.0 b)

lo         Link encap: Local Loopback
           inet addr: 127.0.0.1   Mask: 255.0.0.0
           inet6 addr:  ::1/128  Scope: Host
           UP LOOPBACK RUNNING   MTU: 16436   Metric:1
           RX packets:162  errors:0  dropped:0  overruns:0  frame:0
           TX packets:162  errors:0  dropped:0  overruns:0  carrier:0
           collisions:0  tcqueuelen:0
           RX bytes: 11796   (11.5 KiB)    TX bytes: 11796  (11.5 KiB)

wifi0     Link encap: UNSPEC   HWaddr  00-90-96-B7-6D-3F-00-00-00-00-00-00-00-00-00-00
           UP BROADCAST RUNNING MULTICAST   MTU: 1500   Metric: 1
           RX Packets:0 errors:0  dropped:0  overruns:0  frame:0
           TX packets:3906  errors:0  dropped:0  overruns:0  carrier:0
           collisions:0  txqueuelen:199
           RX bytes:0  (0.0 b)   TX bytes:193347  (188.8KiB)
           Interrupt:201  Memory: dcb40000-dcb50000

---

### Post by eljalill on 2007-03-28
Even if the provider does cable, as long as you get a wireless router going at your end, you have wireless internet.

I guess, you don't have an IP there, which means you are not connected.

Was that with a cable in or without?

---

### Post by Rogue Agent on 2007-03-28
the cable was unplugged.  I can try it again with cable in, but this is at work, so I don't know if it will be different when I try it at home.  Thanks again for being so helpful.  BTW, this might be showing my computer illiteracy, but does the IP address change depending where I am connecting from?  For example, would my IP address be different for home, school, and work?  Ok, well here goes "ifconfig"with ethernet cable plugged  in at work:

ath0     Link encap:Ethernet   HWaddr  00:90:96:B7:6D:3F
           inet6 addr:  fe80::290:96ff:feb7:6d3f/64  Scope:Link
           UP BROADCAST RUNNING MULTICAST   MTU:1500   Metric:1
           RX packets:0  errors:0  dropped:0  overruns:0  frame:0
           TX packets:0  errors:0  dropped:0  overruns:0  carrier:0
           collisions:0  txqueuelen:0
           RX bytes:0  (0.0 b)   TX bytes:0  (0.0 b)

lo         Link encap:Local Loopback
           inet addr: 127.0.0.1   Mask: 255.0.0.0
           inet6 addr:  ::1/128  Scope:Host
           UP LOOPBACK RUNNING   MTU:16436   Metric:1
           RX packets:162  errors:0  dropped:0  overruns:0  frame:0
           TX packets:162  errors:0  dropped:0  overruns:0  carrier:0
           collisions:0  txqueuelen:0
           RX bytes:11796  (11.5 KiB)   TX bytes:11796   (11.5 KiB)

wifi0     Link encap:UNSPEC   HWaddr  00-90-96-B7-6D-3F-00-00-00-00-00-00-00-00-00-00
           UP BROADCAST RUNNING MULTICAST   MTU:1500   Metric:1
           RX packets:0  errors:0  dropped:0  overruns:0  frame:0
           TX packets:45828  errors:0  dropped:0  overruns:0  carrier:0
           collisions:0  txqueuelen:199
           RX bytes:0  (0.0 b)   TX bytes:2268486  (2.1 MiB)
           Interrupt:201  Memory: dcb40000-dcb50000

Also if it helps, when i ran "sudo pppoeconf" it did not ask for a username or password provided by the isp.  It asked for my administrative password.  It scans for Access Concentrators on my connections, and then does the same, but apparently in something called (multi-modem mode).  At the end of it it just says that the Access Concentrator of my provider did not respond and to check my network and modem cables.  It also says that there may be another running pppoe process which controls the modem.

Thanks again for the help.:)

---

### Post by Rogue Agent on 2007-03-30
I don't want to be a bother but can anyone help me figure this out?  I really do not know what to do about this.  Any help would be greatly appreciated.

---

### Post by jdoublep on 2007-03-30
Try thumbing through the steps []("http://ubuntuguide.org/wiki/Ubuntu:Edgy/Networking#How_to_activate.2Fdeactivate_network_connections") to make certain your connections are active.
You might also try statically configuring your card(s) with an IP address. Also, for your wireless, you might try disabling WEP on the router (if it's got WEP enabled) and try connecting that way. If you can connect that way, you'll at least know what the trouble is with the wireless.

---

### Post by Rogue Agent on 2007-04-01
I have just solved the problem of connecting to the internet by reading another thread.  My thanks to everyone who helped me out though.  I used opendns and now I can connect.  Should I worry though that i still see the "oops" page when I try to go to the welcome page for opendns?  Could it be a security issue?

---

