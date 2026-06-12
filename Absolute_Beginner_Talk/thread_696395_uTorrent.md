---
title: "uTorrent"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by H3!ST on 2008-02-14
So, I installed uTorrent with WINE and it asks me to port forward. I'm completely lost. I don't even know where to begin. If someone could instruct/educate me that would be great.

---

### Post by emarkd on 2008-02-14
I don't use uTorrent, but two things come to mind:

1.  Ubuntu's firewall.  If you need to open additional ports, the easiest way to do it is to install Firestarter.  It's in Synaptic.

2.  Router's firewall.  You'll have to check with your router on that one.

---

### Post by H3!ST on 2008-02-14
Why would I need a firewall?

---

### Post by emarkd on 2008-02-14
You already have one.  Ubuntu comes with one and every unneeded port is closed by default.  It's called iptables ifyou want to do a little research.  You can change it's settings my hand if you want to basically learn a new programming language.  Firestarter is much easier. ;)

---

### Post by H3!ST on 2008-02-14
Hahaha, ok so I install Firestarter and my ports are forwarded?

---

### Post by Sinkingships7 on 2008-02-14
no. firestarter is a firewall, and will only close your ports, unless you tell it otherwise.

do you connect directly to your cable modem, or do you go through a router?

---

### Post by emarkd on 2008-02-14
No.  Your ports are already closed.  Use Firestarter to open them.  You'll have to know which ports to open though.

And firestarter is just a GUI to iptables...

---

### Post by Sinkingships7 on 2008-02-14
this i did not know. thank you :)

but my question remains: are you using a router?

---

### Post by H3!ST on 2008-02-14
A router. The box says Westell 327W.

---

### Post by emarkd on 2008-02-14
Here's a screenshot of Firestarter running on my server box.  You can see that under the Policy tab, you just specify ports to open ("Allow Service").

---

### Post by H3!ST on 2008-02-14
So how do I open my ports? And what is a static IP? Do I need it?

---

### Post by Sinkingships7 on 2008-02-14
what the above post says will open the port on your computer. to open the port on your router, you have to access it. 

to do this:


open your web browser and type 192.168.1.1 into the url bar and press enter. if it asks for a username or password, i believe  your username is 'admin' without the quotes and there is no password (i did some research on your router for you).

if opening your computers port with firestarter still gives you a 'port closed' error, then do the steps mentioned above and come back if you can't find out how to open the port.

---

### Post by emarkd on 2008-02-14
See my previous post with the screenshot to open your port(s).  A static IP is one that never changes.  Unless you requested it from your ISP, you don't have one.  But you shouldn't need one for torrenting.

---

### Post by H3!ST on 2008-02-14
So I tried the site and it won't let me log in as admin. I saw the screen shot but I still don't understand. Sorry.:(

---

### Post by emarkd on 2008-02-14
Tried what site?  Are you trying to install Firestarter?  You do that from Synaptic.  System > Administration > Synaptic and search for Firestarter.  After Firestarter is installed and running, that screenshot will make more sense.

---

### Post by H3!ST on 2008-02-14
I had already installed it after you first mentioned it, but when I click on the policy tab there is nothing to view.

---

### Post by H3!ST on 2008-02-14
> **Sinkingships7 said:**
> what the above post says will open the port on your computer. to open the port on your router, you have to access it. 

to do this:


open your web browser and type 192.168.1.1 into the url bar and press enter. if it asks for a username or password, i believe  your username is 'admin' without the quotes and there is no password (i did some research on your router for you).

if opening your computers port with firestarter still gives you a 'port closed' error, then do the steps mentioned above and come back if you can't find out how to open the port.

That site. ^

---

### Post by roboxking on 2008-02-14
A better torrent application is the KTorrent. Just go to Applications->Add/Remove, Make sure the selection at the top right says All Available Applications and under the Internet section, look for KTorrent.

---

### Post by H3!ST on 2008-02-14
The program isn't the problem. Port forwarding is.

---

### Post by emarkd on 2008-02-14
In Firestarter, click on the Policy tab, then click in the Allow Service area, then click the "Add Rule" button in the top left.  There's already an entry in there for bittorrent and it may be just what you need, but if not you'll have to check with uTorrent to see which ports to open.

As to 192.168.1.1, the poster is assuming that your router is at that IP address.  The 192.168.*.* subnet is private and doesn't route, so most people use it for their home networks, but there are three (I think) private subnets.  Even ifyou're using the 192.168 subnet, your router may not be at that address.

---

### Post by SunnyRabbiera on 2008-02-14
but as someone said there are better torrent engines on linux, there is the default bit torrent client, there is ktorrent, there is azureus... 
the list goes on and on.

---

### Post by emarkd on 2008-02-14
> **SunnyRabbiera said:**
> but as someone said there are better torrent engines on linux, there is the default bit torrent client, there is ktorrent, there is azureus... 
the list goes on and on.

Don't leave out rTorrent.  It's the best. :)  But he'd probably still have these issues with any of them.  I had to open the proper ports for rTorrent...

---

### Post by H3!ST on 2008-02-14
Is this what it's suppose to look like?

[IMG]http://img442.imageshack.us/img442/9192/screenshot1ec4.png[/IMG]

---

### Post by emarkd on 2008-02-14
Assuming those are the proper ports for uTorrent's use, yes.  Give it a shot and see what happens.

---

### Post by H3!ST on 2008-02-14
Ok so those weren't the proper ports. How do I find them?

---

### Post by emarkd on 2008-02-14
I don't know anything about uTorrent, but according to [this]("http://www.utorrent.com/testport.php?port=6881"), it needs at least 6881...

---

### Post by H3!ST on 2008-02-14
Ok so what would be my next step?

---

### Post by emarkd on 2008-02-14
Did you ever get your router figured out?  Do you have a router?  If so, you'll have to forward the appropriate ports from your router.  If you Ubuntu box is hooked directly to your modem, this is not an issue.

---

### Post by H3!ST on 2008-02-14
Yeah, it's a Westell 327W. But that's as far as I got. Again, I'm completely new to this stuff.

---

### Post by emarkd on 2008-02-14
This may help: [http://portforward.com/english/routers/port_forwarding/Westell/A90-327W15-06/Utorrent.htm](http://portforward.com/english/routers/port_forwarding/Westell/A90-327W15-06/Utorrent.htm)

It claims to be instructions for your router.  Maybe it'll help...

---

### Post by emarkd on 2008-02-14
That page also tells you how to get the ports out of uTorrent, so maybe you can get Firestarter configured properly.

---

### Post by H3!ST on 2008-02-14
Well I uninstalled uTorrent but thanks anyway to everyone who tried to help.

---

