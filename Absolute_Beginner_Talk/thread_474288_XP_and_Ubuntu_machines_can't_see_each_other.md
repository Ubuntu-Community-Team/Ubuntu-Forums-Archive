---
title: "XP and Ubuntu machines can't see each other"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Doc.Caliban on 2007-06-14
I have two machines connected to a wireless router (via wireless connections)  Both have Internet access. 

From the XP box I can reach the router but not the Ubuntu machine.

From the Ubuntu machine I cannot ping the router or the XP box.

This is driving me nuts.  Ideas?

-Doc

---

### Post by FleetAdmiral74 on 2007-06-15
Ok just for clarification, you have internet through the wireless router, but can't ping said router? That is strange...

---

### Post by Doc.Caliban on 2007-06-15
> **FleetAdmiral74 said:**
> Ok just for clarification, you have internet through the wireless router, but can't ping said router? That is strange...

That's exactly the case.  Totally weird.

I'm on the net now via wireless with the Ubuntu machine, yet I can't ping the router by IP.  This started happening as soon as we switched to wireless.  I'm able to ping and admin the router via the cabled connection, but not wireless.  The XP box has no problem pinging or admining the router, but it cannot ping the Ubuntu box.

-Doc

---

### Post by Seisen on 2007-06-15
Check the router settings and check the firewall settings for xp.

---

### Post by Doc.Caliban on 2007-06-15
> **Seisen said:**
> Check the router settings and check the firewall settings for xp.

Thanks, but it's definitley not the router, and XP is able to do anything but reach the Ubuntu box.  Since it seems that the Ubuntu box is the one having the problem, I'm not too surprised about that bit.

-Doc

---

### Post by Doc.Caliban on 2007-06-15
This goes without saying, but how odd is it that the machine can't ping it's own default gateway, yet it's using it for internet access just fine?

Could the router address be cached somewhere so that when I use it via ping or HTTP it's trying to go out via eth0 instead of eth1 (wireless)?  I can't think of anything other than it trying to use the wrong interface for some reason.

-Doc

---

### Post by Seisen on 2007-06-15
If you can't ping your XP box from Ubuntu its because of a firewall or even the router. I had the same problem when trying to use Samba.

---

### Post by Doc.Caliban on 2007-06-15
> **Seisen said:**
> If you can't ping your XP box from Ubuntu its because of a firewall or even the router. I had the same problem when trying to use Samba.

So lets forget about the XP box for now.  Why can't I ping the router IP that's being used (sucessfully) as the default gateway?  And along the same lines, why can't I access that IP from a browser so that I can admin the router?  (same problem, different symptom)

I can do both instantly if I plug my network cable in and use eth0.

This has something to do with eth1.  The router (WRT54GL running the latest DD-WRT firmware) has been up and stable for months and I can ping and admin it from any number of other computers via either wireless or cat5.  This ubuntu machine with it's wireless connection is the only connection that can't do those things.  

-Doc

---

### Post by Seisen on 2007-06-15
Are you connecting to somebody else's router, this can cause problems if other people around you have open wireless routers.

---

### Post by hoges on 2007-06-15
Maybe the wireless is blocking admin from the wireless connection ie restricted usage? Maybe check to see if it has your ubuntu box ip in the router admin for any options.

Outside of that it could be the firewall on the ubuntu end. Maybe it's enforcing higher security policies for wireless connections. Turn off the firewalls one at a time to narrow it down.

I've noticed that sometimes if you start of using ethernet than unplug it and go wireless, the connections may get confused. This was under XP though, and I haven't seen this under feisty yet. It's most likely a windows bug, but worth checking non the less.

If this doesn't work... I'm not sure what's happening.

---

### Post by Doc.Caliban on 2007-06-15
I appreciate all the ideas, and here's where I'm at with them:  (Forget everything I've said above as it's tending to get people thinking in the wrong direction.)

Ubuntu 7.04 on my laptop can access the router (the default gateway) via ping or http (administration) via the cat5 connection.  (eth0).

It cannot, however, do these things via the wireless connection (eth1).

The wireless connection can access the internet via the router.

The router can be administrated via http or pinged from both XP and Vista both by wired and wireless connections.  

The router is configured properly and has no specific settings regarding the Ubuntu machine's IP/MAC/Etc.

I do not have a firewall installed on Ubuntu unless there's one in there by default.  (?)

The problem seems to be narrowed down to the Ubuntu machine, and specifically to some difference between the eth0 and eth1 interface configurations.

Thanks again,

-Doc

---

### Post by dolphin_oracle on 2007-06-15
This is definenently a weird one.  

I suppose you have checked the IP address of the ubuntu machine and it mathes the rest of the network.  My only guess was that somehow the ubuntu machine is getting its IP address assigned directly from your ISP.  That would be odd, but it matches the symptoms.

---

### Post by Doc.Caliban on 2007-06-15
> **dolphin_oracle said:**
> This is definenently a weird one.  

I suppose you have checked the IP address of the ubuntu machine and it mathes the rest of the network.  My only guess was that somehow the ubuntu machine is getting its IP address assigned directly from your ISP.  That would be odd, but it matches the symptoms.

Good thought, but yes, I've verified the IP settings several times.  At the moment I have two laptops in the house and both are connected to the router and using static 192.168.1.x IP addresses.  Both are configured to use 192.168.1.1 (the router's LAN address) as the gateway and DNS server.  The Internet connectivity works fine on both.

I appreciate that you appreciate the whack-ness of the situation!  It's so frustrating!  I'm trying to get Samba working and be able to admin the router from the Ubuntu box and this problem is killing both of those efforts.

-Doc

EDIT:  I should note that Samba works just fine if I connect the Ubuntu laptop to the router via eth0 (cat5) interface.  This has to be something with the eth1 (wifi) interface.

---

### Post by dolphin_oracle on 2007-06-15
another odd thought, but have you tried disabling the eth0 (wired) connection while the wireless connection is on.  In other words, before enabling the wireless, disable the wired, then enable the wireless.

---

### Post by Doc.Caliban on 2007-06-15
> **dolphin_oracle said:**
> another odd thought, but have you tried disabling the eth0 (wired) connection while the wireless connection is on.  In other words, before enabling the wireless, disable the wired, then enable the wireless.

Solved!  Thanks for the suggestion!

MAN that was a weird one.

Now to get Samba working.  Thanks so much!

-Doc

---

### Post by dolphin_oracle on 2007-06-15
AWESOME!  I really didn't expect that to work!  That definetly goes in the ol' bag 'o tricks.

Glad I could help.

D.O.

---

