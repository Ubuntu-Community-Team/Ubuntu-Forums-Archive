---
title: "Wireless not working"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by BlueEight on 2007-10-30
When I try to connect to my router, it works and I can get online. However, when I'm in the middle of surfing the internet, the connection just stops working. Ubuntu says that I'm still connected to my wireless network, and the router is working, but I can't get to any web pages. Anyone know what's happening?

---

### Post by cmnorton on 2007-10-30
I have DSL. When my PC-to-router connection works and connectivity to the internet does not. I usually reset both the DSL modem and the router. They're both on the same power bar. I wait 1 minute per instructions from the DSL provider. I have also lost connectivity to the router, and I also reset both the DSL modem and the router.

If you have cable or DSL, your provider should help you diagnostically, especially if you can talk to your router.

The only other thing I can think of and it's a stretch is to reduce your mtu count, if you're going over wireless, but I've only had to do that for VPN connections.

---

### Post by BlueEight on 2007-10-30
I did that, but now, I can't even get online. Ubuntu says that I'm connected to my network, and everthing on my network is working, but i still can't get online.

---

### Post by fazavon on 2007-10-30
There is a few things that could be going wrong.

1. Is your ISP having issues, if you are no longer connected to your ISP, you will stay connected to your Router, but not be able to see the rest of the world.

B. Are you on DHCP or Static on your side of the Router? Try using a Static IP you are not now, that way you know for sure you are connected. It may be that Ubuntu thinks you are still connected via DHCP even though you are not. It will not think you are disconnected until your lease is up on you IP and it drops it.

3. Are you sure you have the right drivers for your Card, that could cause it to drop, and or do you have this issue with any other access point it could be your card.

Lets start with theses and work our way down the list.

thanks

//j

---

### Post by BlueEight on 2007-10-30
In ubuntu, does "add/remove applications" require internet? Because I can install new applications, but not use my browser(firefox)

---

### Post by EXCiD3 on 2007-10-30
Add/Remove applications DOES require internet to install applications from.

---

### Post by BlueEight on 2007-10-30
But do you know why I can't use my browser to get online?

---

### Post by BlueEight on 2007-10-30
bump

---

### Post by Het Irv on 2007-10-30
try uninstalling Firefox and reinstalling it. You may have had something go wrong with the settings somehow.

---

### Post by BlueEight on 2007-10-30
The same thing happenes with Iceape.:confused:

---

### Post by Maestro23 on 2007-10-30
> **BlueEight said:**
> bump

Please be patient. Don't bump your post after just 10 min.

Do you have the latest drivers/firmware for your card/router?

Have you disabled IPv6 in your browser or system wide?

What browser are you using?  Any add-ons installed? Tried a different browser?

---

### Post by BlueEight on 2007-10-30
> **Maestro23 said:**
> Please be patient. Don't bump your post after just 10 min.

Do you have the latest drivers/firmware for your card/router?

Have you disabled IPv6 in your browser or system wide?

What browser are you using?  Any add-ons installed? Tried a different browser?

Yes. No, Firefox, no, yes(iceape).

---

### Post by scrooge_74 on 2007-10-30
Use different DNS servers settings, sometimes DNS server from ISP can give trouble.

check [http://opendns.com/start](http://opendns.com/start)

---

### Post by BlueEight on 2007-10-30
> **scrooge_74 said:**
> Use different DNS servers settings, sometimes DNS server from ISP can give trouble.

check [http://opendns.com/start](http://opendns.com/start)


I tried that, but the same thing's still happening.

---

### Post by BlueEight on 2007-10-30
bump.

---

### Post by scrooge_74 on 2007-10-30
Mate try to keep your bumpings to a minimum or you are going to get a ticket from the Admins.

Sorry cant help you at this time

---

### Post by Maestro23 on 2007-10-30
> **BlueEight said:**
> bump.

Did you disable IPv6 like I posted earlier?

> In Firefox:

Open new tab and type: about:config
Scroll down until you see:** network.dns.disableIPv6**

Click it  and make it say TRUE.

Restart FF.



System Wide:

Need to edit: ** /etc/modprobe.d/aliases** (gksudo gedit  /etc/modprobe.d/aliases)

Find the line: ** net-pf-10 ipv6**

Make it look like:  net-pf-10 ipv6 off

Save File and Exit.

---

### Post by BlueEight on 2007-10-30
Thanks! Would you happen to know what it means though?

---

### Post by scrooge_74 on 2007-10-30
You need to open the file Maestro is telling you about and make the change he says, that makes the PC not trying to use IPv6 only IPv4

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

---

### Post by Maestro23 on 2007-10-30
> **scrooge_74 said:**
> You need to open the file Maestro is telling you about and make the change he says, that makes the PC not trying to use IPv6 only IPv4

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

Thanks for the catch scrooge. :)

---

