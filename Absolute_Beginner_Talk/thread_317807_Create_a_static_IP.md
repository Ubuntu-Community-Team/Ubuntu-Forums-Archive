---
title: "Create a static IP"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by devils3cups on 2006-12-13
How do i create a static ip on my network?

---

### Post by Dusty545 on 2006-12-13
You need to access the administration settings on your router for this.  Fortunately, most of them have a GUI to make things nice and simple.

You'll have to check the manual for your router for specifics but there'll be a section (most likely under DHCP) to set an IP range and you should then be able to set a static IP address based on the MAC address of your connection interface.

Hope this helps.

---

### Post by Atomic Dog on 2006-12-13
Or if you want your machine to have an ip you can specify it in the network settings.  If your subnet mask is 255.255.255.0, and it's a small home network, you could just grab something way up in the 192.168.100.240 - 250 range without worry.

---

