---
title: "Linksys router setup. Will I have probs?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Indy452 on 2008-02-23
I need to provide another computer for my kids upstairs so I bought a Linksys etherfast cable/DSL router 4 port at Wal-mart.

Is this going to give me headaches since I run Ubuntu on my computer and the computer upstairs will be W/xp?  I have the dsl modem connected to my computer but I suppose it could be reversed if needed.

When I put in the cd it says must be run some of the files won't open. Is this cd really necessary or can I plug this sucker in and run with it?  I don't see anywhere on the package that its linux compatible.

Thanks for reading and please post your experiences or thoughts.

Neal

---

### Post by rexxxlo on 2008-02-23
linksys are great routers 

look up 
[http://www.dd-wrt.com/wiki/index.php/What_is_DD-WRT%3F](http://www.dd-wrt.com/wiki/index.php/What_is_DD-WRT%3F) 
or 
[http://openwrt.org/](http://openwrt.org/) 

they are flashed versions of the routers that will run linux i love mine it has more options than i can use

---

### Post by FrozenFox on 2008-02-23
Hardware companies in general don't make drivers for linux, with exceptions to ati and nvidia being obvious. Generally, the drivers necessary for your hardware are already integrated into the system by the community. Using a router cd is unnecessary.

If it answers your question, I run ubuntu hardy heron and i have a wireless router. The wireless part is for my sister's windows xp pc several rooms away, and though i could go wireless as well, it's a bad idea for games so i have it directly lined in to my pc. A router doesn't really need drivers on xp or linux. If you are connecting wirelessly, drivers are necessary for the wireless receiver (not the router itself), but if you connect with a chord it is kind of like hooking a phone line into your machine, it's not something very unique as to require drivers, you know?

In short: linux comes with most drivers you need, routers themselves dont really require drivers in most cases but wireless receivers usually do, you can't run a windows driver CD in linux ever, and you should theoretically be A-OK.

---

### Post by torgrot on 2008-02-24
Connect your DSL Modem to the phone jack.  Connect the router to the DSL Modem.  Connect your PCs to the router.  It should be set up by default to use DHCP.  You should be able to open a Web Browser and use http:\\192.168.0.1 to connect to the router.  Everything you need to set is available on the web page.  I have DSL and use a Linksys router with both WinXP and Ubuntu with no problems.  I even have a D-link wireless access point for my laptop.

torgrot

---

### Post by Indy452 on 2008-02-24
Thanks for the links but I guess I should have been more specific in the fact that I bought a wired router. I don't mind pulling a few wires just because I thought it would provide a better quality internet reception too all computers.

So whats with the static IP addresses and stuff I'm reading about in the manual? 

Will I need to use a firewall in the router? I have a firewall installed on the xp computer and of course we all know about the security of linux so that I'm not to worried about my Ubuntu machine.

So maybe I'm making a bid deal of something that is merely a four way switch then?

Thanks 

Neal

---

### Post by torgrot on 2008-02-24
Yes it is similiar to a four way switch, except that it will connect to your provider and take care of other details for you.   I use DHCP with my provider AT&T and unless you have paid for a static IP address, most providers will only allow you to use DHCP.  On your side of the router you can set up static IP addresses, or use DHCP.

torgrot

---

