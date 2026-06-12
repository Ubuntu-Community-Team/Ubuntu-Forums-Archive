---
title: "My newly converted Breezy box has a winmodem..."
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by jorini on 2006-03-21
...so would it be possible to access the internet by going thru an ethernet connection via crossover cable (no router) to a running xp box with an open dial-up connection, and onto the web?

I've got the ethernet connection established (though I can't do anything with it yet except see some files residing on each, from the other.  Can't open anything, but, for now, I'm interested in just porting through.

If such a thing is feasible, please advise, and I'll provide additional detail re where I'm at.

Many thanks in advance.

BTW: My skill level is...what's below noob? Comatose? Brain damaged? 

Maybe it's just the online guides/HOWTOs I've been reading.  It's been awhile since I've felt so over my head.

---

### Post by dermotti on 2006-03-21
If you enable ICA (internet connection sharing) on your windows box, and point your linux towards it as a gateway, that should work fine.

---

### Post by jorini on 2006-03-21
**[COLOR="Blue"]The following in bold is taken from my xp box support manual:[/COLOR]**

[B]To configure Internet options for Internet Connection Sharing
Open Internet Explorer. 
On the Tools menu, click Internet Options. 
On the Connections tab, click Never dial a connection, and then click LAN Settings. 
In Automatic configuration, clear the Automatically detect settings and Use automatic configuration script check boxes. 
In Proxy Server, clear the Use a proxy server check box. 


[/B] I did the above.  Next to the "use automatic config script" checkbox,there was a space for an address (no hint of whether IP or DNS was called for.  I tried 192.168.0.1 (xp box addy) ~.2 (Breezy box addy) and tried ~.3 also just for fun.  In each case, I also put those addresses in the Breezy box gateway addy.  No joy.
-----------------
[B]
To enable Internet Connection Sharing on a network connection
You must be logged on to this computer as an administrator to complete this procedure.

To set up Internet Connection Sharing, run the Network Setup Wizard. 
 Important

When you enable Internet Connection Sharing (ICS), the network adapter connected to your home or small office network gets a new static IP address configuration. Existing TCP/IP connections on the computer running ICS are lost and must be reestablished. For example, if Internet Explorer is connecting to a Web site when ICS is enabled, you must refresh the browser to reestablish the connection. 
To use ICS, users on your home or small office network should configure TCP/IP on their local area connection to obtain an IP address automatically. For more information, see To configure TCP/IP settings. Users on your home or small office network must also configure Internet options for ICS. For more information, see To configure Internet options for Internet Connection Sharing. 
If the computer running ICS is using ISDN or a modem to connect to the Internet, you should select the Establish a dial-up connection whenever a computer on my network attempts to access the Internet check box. 
 Notes

To start the Network Setup Wizard, click Start, click Control Panel, and then double-click Network Setup Wizard. 
For information about the protocols, services, interfaces, and routes that are automatically configured, click Related Topics. 
Internet Connection Sharing is only available when two or more network adapters are installed on the computer. 

[/B]
I also did the above.  Tried setting the Breezy config to DHCP rather than static.  Nothing seems to work.

Thoughts?

---

### Post by jorini on 2006-03-21
Any response would sure be appreciated!

---

