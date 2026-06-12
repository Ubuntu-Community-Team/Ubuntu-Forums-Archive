---
title: "Network Manager - Wifi"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Village on 2007-01-21
Hi there,

I'm having a real headache setting up wifi access on my desktop (running Ubuntu 6.10). It did used to work but I've had to reinstall, previously it just started working once I put Kubuntu and wifi-radar onto the machine, Network Mananger never did seem to work.  I've tried that again but no luck this time.

I have a RT250 based card (Belkin Manufacture F5D7000) 

This time I've also added WPA2 though a Netgear router (DG834N)

I don't know if its the WPA or the Network Manager, under wifi-radar I can see the network but I can't get access to it, 

Is there a good guide somewhere for WPA on Ubuntu or Kubuntu?

Thanks in advance,

Village

---

### Post by riven0 on 2007-01-21
Try this command: **iwconfig**

If it returns with no wireless extension or device, then you will have to install the official drivers through ndiswrapper. So, in that case, try installing the graphical utility and see if it works:

> sud apt-get install ndisgtk

---

### Post by sailor2001 on 2007-01-21
try kwifi manager from synaptics

---

