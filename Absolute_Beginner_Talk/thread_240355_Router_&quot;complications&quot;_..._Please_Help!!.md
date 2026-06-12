---
title: "Router &quot;complications&quot; ... Please Help!!"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by baylorbear on 2006-08-20
When I plug straight into my cable modem, my Apache server runs perfectly.

I'm using DynDNS.com, so I have the ddclient configured to reference their website (checkip.dyndns.org).  It works just fine also.

When I plug back into my router tho (I have multiple machines and they all need to be online) I can no longer access my Apache server via my IP address or the link provided to me by DynDNS.com.  Apache will still run internally and on the intranet, however.

I have port 80 forwarded to my desktop running Apache... but still no dice.

Can anybody help me solve this???

---

### Post by Haegin on 2006-08-20
What router are you using? I have had problems with the D-Link routers when I try port forwarding. The model would also be helpful.
Can you try installing a web server on another machine (if you have *shudder* windows xp pro you could try IIS as its easy to install (though not as easy as apache on ubuntu)) then check if that works - it shouldn't really but its important to test.

---

### Post by baylorbear on 2006-08-20
Actually, yes... I have tried from another machine using IIS.  On my network, I have my Ubuntu box, two Windows laptops, and two Mac Powerbooks.  On the laptop with IIS, same problem.  No access outside the network.  

Router Information:

Netgear MR814
Firmware:   4.14 RC4 Dec 11 2003
(the latest firmware available for this router)

---

### Post by Haegin on 2006-08-21
Well its definatly a problem with your port forwarding so go here: [http://www.portforward.com/](http://www.portforward.com/) and check you have set it up correctly. I think some ISPs block certain ports so you may have to change the port apache is running on (and the forwarded port)
I must say I haven't had much success with my D-Link.
Good luck

---

### Post by baylorbear on 2006-08-21
Crazy thing is -- the router IS set up correctly to forward the ports.

And my ISP doesn't block any ports -- I can plug my box directly into the modem and it works just fine.  But that isn't a permanent solution as I have other computers that need to access the net...

---

### Post by baylorbear on 2006-08-21
Bump ... still seeking an answer!  Please post input if you can!

Update:  I've gone thru the steps at [www.PortForward.com](www.PortForward.com) for the 10th time now and still not working...

---

