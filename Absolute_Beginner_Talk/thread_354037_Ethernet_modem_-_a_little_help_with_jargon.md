---
title: "Ethernet modem - a little help with jargon?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by whitefort on 2007-02-05
I apologise in advance for how basic this question is. 

I've just discovered that my USB modem is no good with Ubuntu, and that I need an Ethernet modem.

However, browsing round the websites, I find myself totally confused by the terminology.  I mean, is a 'modem router' another way of saying 'modem'?  Or is it something different from a modem altogether, but you plug a modem into it for some reason?

What I WANT is to have two Ubuntu machines - One will be connected to the internet by the nice new ethernet modem, and the second will be connected to that machine by Ethernet cable, sharing the internet connection (and files and printer).  

But what ***EXACTLY ***do I need to buy?  

Oh, and another stupid newbie question - I'm told that I'll have to configure the Ethernet modem by visiting a web page?  But...  How can I visit the web page before the modem is configured and working?   :confused:

---

### Post by annda on 2007-02-05
if you want to connect more than one computer you will need a router (it splits the internet connection) WITH a modem (it connects to the internet), and the best way to do this is to get a modem router. it will be just one piece of hardware - plus the modem integrated in the router will connect to the internet as soon as it is switched on, so there will be no problems with ubuntu compatibility here: your computers will just use the connection established by the modem router.

you configure the Ethernet modem via an internal "web page" that sits in your modem router, NOT on the internet. it's basically an interface to enter all the data you need to access your ISP, like username and password.

p.s. i assume you have a DSL connection, not dial-up.

---

### Post by whitefort on 2007-02-05
Thanks, that's helpful.

I was just getting more and more confused - I knew I needed a modem, but did I need a modem AND a router - or a modem router?  And I didn't even know what a router was anyway!

I'll start browsing for modem routers - thanks!

---

### Post by Daveth on 2007-02-05
well, I can answer part of your question. You will need a router- I have an adsl router for broadband. This will usually come with a phone cable terminated at 1 end by a phone plug (to go into your main or extension phone wall socket) and the other end, which goes into your pc's ethernet port round the back, with an RJ45 termination. PC to PC goes via a CAT5 ethernet cable, with RJ45's at either end. CAT5 cable is available in a range of lengths, colours etc - just Google network cable. Not tried networking pcs, so someone else will have to try that one. My single system works just fine.
The web address section is just typing the router's own network address into the address box of your browser- this brings up the configuration page for your router, and allows you to set levels of protection, network addressing etc. They are usually passworded and with a user name. You can set up a static IP address for your PC rather than accept the dynamic one your internet provider will give you. This has some network advantages. Though specific to the BT 205, this page:
[http://corz.org/comms/hardware/router/bt.voyager.205_router.how-to.php](http://corz.org/comms/hardware/router/bt.voyager.205_router.how-to.php)
has much helpful info on the principals involved. Many of the routers have web pages devoted to their tweaking.

---

### Post by whitefort on 2007-02-05
Thanks, Daveth.

I'm just a few mouse clicks away from buying my modem router from Amazon.  I already have my 2 PCs networked with an Ethernet cable.  A Ubuntu machine connects to an XP machine via the cable, and the XP machine connects to the internet via my USB modem.  The Ubuntu machine shares the XP's internet connection via the cable.

Today I considered ditching XP totally, but thankfully I tried the live CD first and discovered that Ubuntu couldn't see the USB modem.  This means at present I can't dump XP without also dumping my only connection to the internet!

It's a bit of an adventure for me, this Linux stuff.  I'm not finding any of it particularly smooth or easy, but I'll get there eventually.

---

### Post by jml on 2007-02-05
There are several advantages to connecting both of your computers through a modem router.  Fisrt, it is not necessary to keep the gateway computer (the one connected directly to the modem) on all the time.  Second, the router portion of the device acts as a very basic hardware firewall.  Only the ip address of the router is exposed to the internet.  Your computers IP addresses are not.  Just be sure to change the default Administrator password from the default to something harder to guess.

Joe

---

### Post by whitefort on 2007-02-05
> **jml said:**
> Fisrt, it is not necessary to keep the gateway computer (the one connected directly to the modem) on all the time. 

That will be a definite advantage.  Does this mean I'll need to have one wire from each PC running into the router, and then another wire between the PCs, for file sharing, etc?  I think I'll need to add a network card and cable to my order.

Thanks.

---

### Post by Jussi Kukkonen on 2007-02-05
No. One wire from each computer to router is enough. File sharing will be possible with that setup.


EDIT: To clarify all this: When you have a router you have your own little LAN (local area network), where all the computers can see each other. The router is the only thing connected to the internet -- it will be configured so that machines in the LAN will still see the internet, but machines in the internet cannot see your machines. In short: any machine in the LAN sees all machines in LAN and internet.

---

### Post by Jamface on 2007-02-07
I have the same kind of setup, 2 computers connected with a ADLS modem router.  My internet connection works well running Windows XP on both machines.  On Monday I installed Ubuntu 6.10 as dual boot on the gateway machine and set up the network connection as per the instructions in Ubuntu.  But FireFox does not seem to work properly.  When I put in a URL (including [www.ubuntu.com](www.ubuntu.com)) the wait circle spins for a couple of minutes, then I get an error message which says the connection was timed out because the URL site did not respond in time.  The same happens when I try to use the installed search engines. 
I then went through the ADSL modem router setup again which I can access from Ubuntu, trying various options.  None solved the problem.  I then went through the Ubuntu network setup again, trying different options, including Static and Dynamic settings (not that Ireally knew what I was doing!).  I have Ping tested the connection from within the modem router and it seems to be OK.
Strangely, there is one website which i have been able to access - BP PLC, but when it suggested via a popup that I needed to upgrade my flash software the same problem arose.
Would I be better to instal Ubuntu 6.06?  How difficult is this to do over version 6.10?
I would be very grateful for any help anyone can give me.

---

