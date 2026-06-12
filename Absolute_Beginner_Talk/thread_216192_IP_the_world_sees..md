---
title: "IP the world sees."
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by wildseven on 2006-07-15
Is there a command that will show my my ip the world sees and not my LAN ip? ifconfig shows me the ip my dchp gave me.

---

### Post by [S|G] on 2006-07-15
I think it is easier for you to use a web page that checks your IP address:
[http://whatismyipaddress.com](http://whatismyipaddress.com)
[http://www.showmyip.com/gb](http://www.showmyip.com/gb)
are some sites you can check that

---

### Post by wildseven on 2006-07-15
Thank you, I'm glad you replied, but I already know about the websites. I'm just curious if there is a terminal command.

---

### Post by Ubunted on 2006-07-15
If you have a router you can change its MAC address. Most broadband connections bind IP addresses to MAC addresses, so if you can change it you'll get a new IP.

However this is not reccomended as there is the possibility that you will duplicate someone else's MAC address and cause problems. For this reason routers tend to have an option to clone your PC's MAC address.

The alternative is to hook up a new router, NIC or unplug your modem for 24 hours so the DHCP servers release your IP.

---

### Post by philippe_carlo on 2006-07-15
```

sudo apt-get install traceroute
traceroute google.com 

```

The second 'hop' shows your IP address.

---

### Post by steve.horsley on 2006-07-15
If you are using a modem, then the IP address will be one actually on your computer, and the command **ifconfig** will show it. 

If you are behind a router, then that router is probably doing address translation. In this case, your PC will have no idea that it is being translated, let alone what it is being translated to.

---

