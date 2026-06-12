---
title: "Wireless Internet- Getting it working"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Pollo del Polvo on 2007-03-30
I just recently installed Ubuntu Edgy on my Ibm ThinkPad T43. When I pull up the Network Settings (System>Administration>Networking) a wireless connection shows up as one of the connections. I then set it up with the ESSID of the local wireless internet, entered the WEP key and set it to Auto Config (DHCP). When I then look at the connection Properties of eth1 it shows a signal strength of over 90% however no packages are being received. And when I try to access the internet via firefox I get a "Server not found" error. Any ideas as to where the problem could be?

---

### Post by jdoublep on 2007-03-30
If you're able, disable the WEP protection on your router for just a few moments to test if you can connect to an unprotected wireless network. I almost guarantee you'll find the issue is with the WEP key.

I had the same trouble and tried manually inputting the hex in various .conf files to no avail.

On a whim, however, I updated to the Fawn beta on release day and once it installed - my wireless, with WEP protection, worked flawlessly. Further, Fawn supports wireless roaming, so you can hit open wireless hot-spots with ease. Installing Fawn also fixed some SMB issues I had with my Ubuntu box not being able to access Windows shares on my home network.

There's no guarantee the upgrade will fix your issue, but I played around with Edgy for a month trying to get the WEP key to take...no luck. So I'd give it a try (provided you can determine that you're able to connect to an unsecured wireless network.

Good luck.

---

