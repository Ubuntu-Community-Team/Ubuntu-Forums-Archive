---
title: "running Deluge"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by jhvillegas2 on 2008-01-08
I am trying to get Deluge to start downloading a file, but the process is blocked for some reason.  I have adjusted my port range to that which is recommended.  Still no go.  Any suggestions are welcome.

Thank you kindly,
jhvillegas2

---

### Post by bumanie on 2008-01-08
Is it blocked or is it just that there are no seeders/peers on line at present for the particular torrent?

---

### Post by rune0077 on 2008-01-08
Probably a firewall issue. If you're using Firestarter, make sure the port(s) used by Deluge are open.

---

### Post by alx010 on 2008-01-08
Under Edit>Preferences>Network, click on the Test Active Port button to see if you're blocked.

---

### Post by jhvillegas2 on 2008-01-08
The output of the Test Active Port function states that the first port is blocked.  I didn't test the others--there are quite a few of them.  And I am not running Firestarter, so that is not the culprit.  Any other suggestions?

---

### Post by rune0077 on 2008-01-08
Well Firestarter is actually just a frontend GUI to the default firewall, so it probably still is the culprit. Firestarter makes it much simpler to open ports for services, so I would suggest downloading it from Synaptic. It can be done by editing files as well, without Firestarter, but I'm no expert on this, so I won't try to give you any advice about it. If you do install Firestarter, let us know, I'll help you open the ports if you don't know how to use it (it's not that complex though)

---

### Post by philinux on 2008-01-08
got mine set to random ports, not touched firestarter, iptables or router. It just worked first time.

---

### Post by alx010 on 2008-01-08
From the FAQ on the Deluge site,

> Which ports should I use?

The official ports for BitTorrent are 6881-6889, but most ISPs block or at least throttle those ports, so users are encouraged to use a port range of something between 49152 and 65535.

So I would also suggest using Firestarter to set your ports. BTW, I just updated to the latest version of Deluge, (not the one in the repositories) & seem to be getting a better download speed with the same settings.

---

### Post by rune0077 on 2008-01-08
Mine is set to random ports as well, but each time I use it I need to check which port is used and then open it through Firestarter, otherwise it's a no go.

---

### Post by Steveway on 2008-01-08
Do you have a Router?
You need to forward those needed ports in it to your Pc. (Look in your Routers manual for information of how to do this.)
If even that doesn't help then it's most propably your ISP that is blocking those ports.
Use other ports or talk to your ISP that they accidently are blocking those ports and you can't get your newest Linux-distributions etc..

---

