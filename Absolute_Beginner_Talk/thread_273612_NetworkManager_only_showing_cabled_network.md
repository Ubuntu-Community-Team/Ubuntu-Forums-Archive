---
title: "NetworkManager only showing cabled network"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by pisapiag on 2006-10-08
I got Applet NetworkManager 0.6.2 installed. I have a Netgear WG311T wireless NIC and an Ethernet NIC. Somehow, I got the wireless NIC to work and it wasn't easy. I actually don't remember how I finally did it but it was no picnic. These forums helped a lot. The quirk is that Applet NetworkManager 0.6.2 won't see the wireless card even though it's active and working nicely. It only sees and shows the wired network connection. 
How can I make it see the wireless connection?

---

### Post by MikeBenza on 2006-10-08
I had a similar problem.  This solution seemed to work for me, but correlation isn't causation:

Go to System -> Administration -> Networking.  Select the wireless device, and go to Properties.  Write down any of the values.  Clear everything.  Leave everything blank that you can (of course you can't clear the DHCP / Static option, but I left it on DHCP).  Reboot.  The wireless network manager should appear.  You can then click on it to view available wireless networks and connect to your favorite.

This is only from observations -- I haven't set out to test this definitely.  If it works, it works.

(BTW -- are you in Pisa?  I'm in Florence)

---

### Post by blx_286 on 2006-10-08
> **pisapiag said:**
> I got Applet NetworkManager 0.6.2 installed. I have a Netgear WG311T wireless NIC and an Ethernet NIC. Somehow, I got the wireless NIC to work and it wasn't easy. I actually don't remember how I finally did it but it was no picnic. These forums helped a lot. The quirk is that Applet NetworkManager 0.6.2 won't see the wireless card even though it's active and working nicely. It only sees and shows the wired network connection. 
How can I make it see the wireless connection?

I have the same problem and I have an AirLink card. I read in another thread to edit the interfaces file in terminal 

```
sudo gedit /etc/network/interfaces
```

and comment everything out, except the local loopback, with an "#" at the beginning of each line. I tried that too but it didn't correct the prob.

---

### Post by pisapiag on 2006-10-09
To Mike
No, I'm not from Pisa. I'm from Montreal, Quebec, Canada. I would have tried your solution if you woudl have guaranteed me it would have worked. I spent too much time getting this wireless card to work to mess with it. Thanks anyways.

---

### Post by Henry Rayker on 2006-10-09
Well, his reason for having you write everything down is so that, if it doesn't work, you can go back to the way it was before you tried.

There are very few guarantees with Linux. Sometimes you just have to jump in, get your hands dirty and pull your hair our.

---

### Post by tytus on 2006-10-09
> **MikeBenza said:**
> 
Go to System -> Administration -> Networking.  Select the wireless device, and go to Properties.  Write down any of the values.  Clear everything.  Leave everything blank that you can (of course you can't clear the DHCP / Static option, but I left it on DHCP).  Reboot.  The wireless network manager should appear.  You can then click on it to view available wireless networks and connect to your favorite.


Worked for me. Initially after installing Network Manager did not show any networks. Once I cleared networking and rebooted it showed me the wireless networks in the area.

---

