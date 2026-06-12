---
title: "netgear"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by linex on 2007-01-30
hi
i've finally decided to install ubuntu. i have a gateway mx5464 and there are huge issues with network card. so i decided to buy a "fully supported" wireless card. i bought the netgear wg511t.

i insert the card and now i don't know what to do. i have a wireless home network with wep protection.

can someone guide me through this please

thanks

---

### Post by mikewhatever on 2007-01-30
Try this [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/internet.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/internet.html)
If,as you say, the card is fully supported, all you'd need to do is: System->Administration->Networking, select Wireless Connection, click Properties, and enter your network name and WEP.

---

### Post by linex on 2007-01-30
thanks
i got connected from "networking"

now, how do i scan for other available networks?

---

### Post by bikeboy on 2007-01-30
I'm not sure whether this program supports your card or not, but Network Manager is brilliant when it works. It automatically chooses the strongest signal wireless network, or wired if it's available.

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by mikewhatever on 2007-01-30
You need to install one of the network managers. Gnome NM is probably the first choice.

sudo apt-get install network-manager-gnome

You need to disable the wireless in the System -> Networking to use it, and then reboot. Hopefully, :D  then you'll get a working icon on the top panel.

---

