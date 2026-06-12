---
title: "Torrents"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by prenticematthew on 2008-03-03
I downloaded Transmission today from Synaptic and it starts up fine but when I try and start a torrent download it just sits there.  I use uTorrent on my Windows partition and it worked fine without any extra interventio:confused:n.  What could be the cause here?  BTW I am using 7.10 64 bit edition and also have firestarter installed on my system.

---

### Post by Moop on 2008-03-03
Have you checked to see if your incoming port is open? You can look in Transmission under Edit-Preferences.

---

### Post by prenticematthew on 2008-03-03
It says the listening port is 9090.  How can I open this port in firestarter and/or in the OS?

---

### Post by Moop on 2008-03-03
I don't use firestarter but there should be a way to allow a port or service access to a open port. In most firewalls you would specify transmission using whatever port. 

If you're using a router that has a firewall you would need to open the port there also. But if you had a router firewall you wouldn't really need firestarter.

---

### Post by wolfen69 on 2008-03-03
Firestarter users manual pdf [http://www.fs-security.com/docs/fs-manual.pdf](http://www.fs-security.com/docs/fs-manual.pdf)

---

### Post by WSmart on 2008-03-03
There's a trick with Firestarter.  You have to right click the Allow Services window in the Policy tab and choose Add from there.  The menu option isn't active for some reason.  I set an inbound policy that way and that's all I did and it works.  

I'm using Azureus, also available from the synaptic manager, but you should have a test feature that allow you to test your port.  

I'm looking around to see if there's a torrent option for synaptic downloads.   Would be cool.

---

