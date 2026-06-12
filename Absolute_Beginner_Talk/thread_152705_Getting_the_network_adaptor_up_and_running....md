---
title: "Getting the network adaptor up and running..."
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by MarkTBSc on 2006-03-30
Thanks to the skilled assistance of the chaps and chapesses here on the board I now have my C1 looking beautiful and purring like a kitten. The next step I'm having a little difficulty with is sorting out its network connection. I have four available network adaptors... Three Cabled and one Wireless. A PCMCIA D-Link Neteasy adaptor, a USB Netgear adaptor, A USB Sitecom adaptor and a PCMCIA 11b card from Bluetake.

Breezy seems to see all these just fine and can give me data back from them, however no matter what I alter in the network settings (Putting in IP's and configuring WEP keys etc.) It won't seem to access the net.

I would have included data dumps from the screen here if I could but, no net connection to the laptop.

Any suggestions guys?

---

### Post by jamesr on 2006-03-30
I believe that it will be easier with the wired.

How are you connecting to the internet?
direct to broadband modem or via a router?

---

### Post by MarkTBSc on 2006-03-30
Router. I have a wireless router that connects via cable to my Desktop machine and vie either wireless or cable to my laptop. From there it runs off to a cable modem and thence to the Internet.

---

### Post by jamesr on 2006-04-01
please post the output of ```
sudo ifconfig -a
sudo iwconfig -a
``` once the NIC is in the system

also the output of ```
dmesg | grep eth
```

---

