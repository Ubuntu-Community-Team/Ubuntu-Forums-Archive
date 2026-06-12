---
title: "Big Question: Wireless"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-05-07
Hello,

I have a Dell Latitude X300 with a built in wi-fi connection but I cannot get it to work.

Well, to be honest I have absolutely no idea where to actually start and I all the guides I have found are extremely confusing.

Could someone please give me some help?

Many thanks.

---

### Post by gummylindz on 2006-05-07
I just got a new laptop with built-in wifi and I think it depends on the connection you have with your router.... like if its secured or with a wep code or something.....

i'm very new to ubuntu so i can't give you loads of detailed and knowledgable help as you might have noticed hehehe... but i will tell you that for me it worked by just configuring the network to the router, through the router's homepage and also through the network.

i hope that wasn't more confusing for you :confused: ummm okay this is my case:

i have a wifi router, and connected to it are 2 computers and my laptop. we were getting real slow internet and we checked out on the router page the dhcp users and there were neighbours connected to our router (i live in a block of flats, and it does happen with wireless) because we had an "open" connection. so we changed to wep, and put in a code, so any computers wanting to connect to our router via wifi have to have this code put in.

when i got my new laptop i just set it to wep and put the code in and it worked!

hope i helped........ i'll be very thrilled if i did as im a newbie ubuntu user :D

---

### Post by Rinzwind on 2006-05-07
Me too.

I have my router set up with a WEP Key (128 ) and all I needed to do was to add the SSID and WEP key and it worked.

The SSID is the name you gave to your network and looks like it is casesensitive(?)


Oh I am using Dapper but it did work with Breezy when I was using that.

I hope you do get it working tho. It sucks having no connection when you want some cool games :KS :KS 

I am using a Dell too. An Inspiron 9300. I think that probably has the same WIFI card.   BRB gonna have a check for it


edit:
Network controller: Intel PRO/Wireless LAN 2200

And it's exactly what I have too!

So it should work out of the box on Dapper and Breezy :(

---

### Post by Dr Von Bon Bon on 2006-05-07
But how do I actually get to the point where I put the wep code and stuff in?

When I have taken my laptop to places where they have no code on their wireless I still can't connect.

WHere do I connect from?

---

### Post by gummylindz on 2006-05-07
menu: **System - Administration - Networking**

there you should then **Configure** whatever you have at the mo, and somewhere in there, like a **Properties** menu or something, you should find it.

I'd have a check for you manually, but I can't right now as I'm having a problem with my hostname, I changed it and now can't get into ANY administrative processes... check my thread, and pleas help if you can, because I can't even install updates or run terminals!

---

### Post by Rinzwind on 2006-05-07
Yes.
System, Administration, Network
Type your sudo password
Click the wireless network connection
Properties.

---

### Post by Papa-san on 2006-05-07
I had a huge problem with wireless in my Dell. I actually included some links in my signature to simplify things. Start with the wireless guide. It will take you through what you should check into anyways, so just follow it, and post any results that you get that might help us narrow down your issues. My drivers were not installing, and I'm willing to bet this is where your issue begins.

(I have been known to be VERY wrong, however!) :rolleyes:

---

### Post by monomaniacpat on 2006-05-07
You first need to have the drivers installed. If they aren't your computer won't understand how to use the hardware and wireless won't show up under networking. You have two options: [ndiswrapper]("http://ubuntuforums.org/showthread.php?t=81461&highlight=ndiswrapper-utils") (the easiest option, but not one that worked for me) or open-source drivers, which you can find [here.]("http://linux-wless.passys.nl/") 

Let us know what card you are using for more help.

Yours,

mono.

---

### Post by Dr Von Bon Bon on 2006-05-07
It doesnt list anything about wireless on the networking menu.

Any ideas?

I tried following the wireless guide but it was overwhelming.

---

### Post by Dr Von Bon Bon on 2006-05-11
Okay,

I'm not sure if my wireless card is actually being recognised. Could someone please tell me how to check if it is please?

---

### Post by Rinzwind on 2006-05-11
Type **ifconfig** in a console

eth1 should be a wireless.

Something like this:

eth1      Link encap:Ethernet  HWaddr 00:12:F0:A1:00:04
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fea1:4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4726 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7042193 (6.7 MiB)  TX bytes:559049 (545.9 KiB)
          Interrupt:201 Memory:dfcfd000-dfcfdff

---

