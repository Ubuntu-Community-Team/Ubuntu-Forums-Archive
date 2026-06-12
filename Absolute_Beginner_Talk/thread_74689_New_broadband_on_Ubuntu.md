---
title: "New broadband on Ubuntu"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by mokeyjoe on 2005-10-12
I was wondering if there was any way to set up a new broadband connection using Ubuntu Hoary (or breezy for that matter - I'm not averse to upgrading). All the things I've read seem to suggest that I need to set up the connection on a Windows machine and then I can use it on my Linux box. Mainly because of the installers provided by the ISPs it would appear.

Is there a UK provider that will let me set up on a Linux machine. I only have one computer and its running Ubuntu.

---

### Post by Kapre on 2005-10-12
[QUOTE=mokeyjoe]I was wondering if there was any way to set up a new broadband connection using Ubuntu Hoary (or breezy for that matter - I'm not averse to upgrading). All the things I've read seem to suggest that I need to set up the connection on a Windows machine and then I can use it on my Linux box. Mainly because of the installers provided by the ISPs it would appear.

Is there a UK provider that will let me set up on a Linux machine. I only have one computer and its running Ubuntu.[/QUOTE]

mokeyjoe - from the previous post that I've read, you have a USB modem (zyxel 630) and I think this is not yet supported. I'm not from the UK and not using a USB modem. Try installing Breezy as this "might" have the support (drivers) for your modem.

K

---

### Post by mokeyjoe on 2005-10-12
Oh no, this is different. I've moved to a new house. The previous modem was one I was temporarily using at my parent's house to set up Ubuntu. My new place has no internet at all and I do not have a modem of my own. 

I don't mind buying a modem if one isn't provided by my ISP. I just want a provider that will set me up from scratch without requiring a Windows machine. 

For the record, the USB modem autodetected and worked straight away, but the broadband connection had obviously been set up on Windows. I want to set up from scratch using only Ubuntu - is there a provider that will do this?

---

### Post by karuptdata on 2005-10-12
I know that here stateside there not alot of ISP's out there that would support linux any broadband service should work..all you would need to do is specify a couple of settings in your networking tab and if you get loss theres a ton of awesome people that dont mind helping here! 

Best Regards!

---

### Post by Kapre on 2005-10-12
[QUOTE=mokeyjoe]Oh no, this is different. I've moved to a new house. The previous modem was one I was temporarily using at my parent's house to set up Ubuntu. My new place has no internet at all and I do not have a modem of my own. 

I don't mind buying a modem if one isn't provided by my ISP. I just want a provider that will set me up from scratch without requiring a Windows machine. 

For the record, the USB modem autodetected and worked straight away, but the broadband connection had obviously been set up on Windows. I want to set up from scratch using only Ubuntu - is there a provider that will do this?[/QUOTE]

mokeyjoe - Almost all ISPs here in Canada says they do not support linux (even my ISP says that - so Karuptdata is correct). But I'm using Linux. I guess it just so happens that because they are big companies they have somesort of a tie-up with M$. As I said earlier, I'm not from the UK but I guess (if your going to use ADSL), you can join an ISP there and when they give you the username and password, just set it up using PPPOE conf and it will connect you (they just wont give tech support)

K

---

### Post by Zimmer on 2005-10-12
Hi.
My advice is to buy a ADSL router/modem such as a Netgear DG834UK.

Ubuntu will detect the connection through your ethernet card and you will need to enter very few details into the router (which uses a web browser interface) such as your user id and password provided by the ISP,(and maybe 2 DNS addresses) as it will autodetect most of the other settings. It is as simple as that. You do not need any fancy installer software from your ISP...
The router acts as a hardware firewall, too.
I have been using such a router for 3 years now, and well over 18 months with Linux.
My ISP , BTW,  is Nildram... now part of the PIPEX empire...

Go here if you want to compare ISP's 
[http://www.adslguide.org](http://www.adslguide.org)

Regards

Zimm

---

### Post by poofyhairguy on 2005-10-12
My cable internet service required using a browser to set it up. So, Linux works fine there!

---

### Post by SilentCacophony on 2005-10-12
Even if the ISP says that you need thier software to set up a modem or router, you can generally set them up manually. Most of them can be accessed by web browser to set them up. That's how I initially set up my router and modem.

---

### Post by mokeyjoe on 2005-10-13
Thanks for the response guys. I'll try setting it up on Ubuntu (may need some halkp though ;) ).

If all else fails then I can resurrect my old win98 machine to do the dirty work for me, although I would have to make a 200 mile round trip to pick it up. :)

---

