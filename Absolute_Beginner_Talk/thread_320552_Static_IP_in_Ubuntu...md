---
title: "Static IP in Ubuntu.."
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by CAN-CAN on 2006-12-17
Is there a detailed guide which I can follow to set a static IP in Ubuntu?
I have the Zyxel Prestige 660H router.

---

### Post by macogw on 2006-12-17
You should just have to go to System > Administration > Networking and turn off DHCP, then tell it what the IP address you want is.  I think that only changes it on your intranet though.  For the outside world, your ISP has to set your static IP.  If you're trying to run a server though, there's [http://dyndns.com](http://dyndns.com) which will update your IP address to your domain name when the IP changes.

---

### Post by CAN-CAN on 2006-12-17
Should I open some ports for synaptic etc?
Is there a website which can give me information about port forwarding on linux programs?
For windows the website is [www.portforward.com](www.portforward.com) .

---

### Post by maxamillion on 2006-12-17
You shouldn't need to port forward if you are just using synaptic to install packages. Port forwarding is generally for when you are running server applications such as apache for web, etc.

---

### Post by msak007 on 2006-12-17
Just a word of advice. If you use Network Manager to connect to your network, it is not currently compatible with static IPs. The only way to set a static IP in that case is if your router supports it (assigning specific MAC addresses a static IP). If you don't use Network Manager, then macogw's advice of setting your IP using the Networking administration tool should do the trick.

---

