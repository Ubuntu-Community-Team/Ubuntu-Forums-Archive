---
title: "Brand new WHR-HP-G54 wireless router."
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Stickfigure on 2007-10-08
Well, I need to set up a brand-new wireless router, a Buffalo WHR-HP-G54 Wireless G MIMO Performance router.  I don't need to connect this computer to the internet through wireless, but there are others here that need the help.

I have no idea how to set up a router.  I am absolutely working with no tools other than an inquisitive nature and a strong need to not be beaten by this router.  However, I don't know where to start, or how to set things up.  I call out to you, the helpful folk of Ubuntu forums, to assist me with this process.

So... there it is.  Help me, please.

---

### Post by cameronw on 2007-10-08
Consult your manual for the internal IP address usually 192.168.1.1 or something. Type [http://xxx.xxx.xx.xx](http://xxx.xxx.xx.xx) ( the internal IP address ) into your browser and it will prompt you for a password - usually something like username: admin password: admin and you will enter the routers config.

I do not have a wireless network but if I recall seeing in the "New Features" of Ubuntu Feisty 7.04 it will automatically pick up wireless signals Go to System > Administration > Network and check to see if Wireless is enabled on the computer that will be receiving the signal. If not you may also have to find the suitable Linux drivers for your Wireless Card.

---

### Post by Stickfigure on 2007-10-10
The other computer attempting to hook up is a windows box, and thus far is unable to initialize it's wireless connection.  No signal is being detected.  So now what?  DD-WRT?

---

### Post by cameronw on 2007-10-11
Have you tried going to network in the Control Panel and starting a new network connection on the side pane there, assuming you run Windows XP? It should guide you through it.

---

