---
title: "Connecting to VirginMedia Broadband"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by onemorepromethean on 2007-09-03
Hi there

I've recently installed Ubuntu 7.04 on my new laptop, which dual boots with Vista.

However, I can't seem to configure my internet connection (Virgin Broadband, through ethernet connection to modem). The Virgin installation CD isn't linux-friendly, and I'm new to Ubuntu myself.

I've tried copying and pasting the IP address, subnet mask etc details from the connection on this computer, but to no avail.

Does anyone have any idea how to fix this?

Thanks in advance
Jim

---

### Post by cawill on 2007-09-03
Does the network manager say that there is a wired network connected? Also what router/modem are you using?

---

### Post by onemorepromethean on 2007-09-03
Thanks for replying. Yeah, it says wired connection.

Its a Realtek RTL8139 Family PCI Fast Ethernet NIC, supplied by Virgin.

Jim.

---

### Post by LooieENG on 2007-09-03
> **onemorepromethean said:**
> Thanks for replying. Yeah, it says wired connection.

Its a Realtek RTL8139 Family PCI Fast Ethernet NIC, supplied by Virgin.

Jim.

I have the same one. You want to select cable modem, not ethernet.

---

### Post by onemorepromethean on 2007-09-03
Thanks for replying LooieEng.

I can't see the ethernet/cable option anywhere. I'm looking on the properties of the wired connection in the 'network settings' thing.

Where should I be looking?

---

### Post by onemorepromethean on 2007-09-03
I should probably add that as yet I haven't found where to enter my ISP username and password etc?

---

### Post by onemorepromethean on 2007-09-03
*bumps and apologises*

---

### Post by LooieENG on 2007-09-03
Well, I had to choose cable modem on PCLinuxOS, it was setup automatically on Ubuntu.

But go to System > Administration > Network.

Mine looks like this (I'm with Vermin Media too)

[IMG]http://xs319.xs.to/xs319/07361/Screenshot-Network-Settings1.png[/IMG]

[IMG]http://xs319.xs.to/xs319/07361/Screenshot-Settings-for-interface-eth0.png[/IMG] <<<<< Properties for wired connection

---

### Post by onemorepromethean on 2007-09-03
Ooh dear, thats what I had and it's still not connecting.

Did you not need to enter your username/password etc? 
Hmm, wonder what else it could be.

---

### Post by philinux on 2007-09-03
Look under System > Admin Network

and click the tab DNS. under search domains is a web address. Make a note of this and open a browser window and type it in. This is the webpage of the router. Here is where you will "somewhere" enter your username and password. Mine us a 2wire router so it will be different from yours.

---

