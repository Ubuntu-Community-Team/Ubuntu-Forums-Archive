---
title: "Internet"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by NaCl on 2007-04-11
I don't know what's going. I installed a fresh ubuntu 4 days ago. I didn't mess with the network setting. From time to time I notice webpages being unresponsive, but then I can download from IRC bots with good speed. What can I do to solve this problem?

---

### Post by tipsqueal on 2007-04-12
Do you have another PC? If so, have you noticed the same or similar problems on it? Do you have any network hardware, for example routers, switches, hubs, network card, etc.? If so have you checked to make sure they are all connected/installed/configured correctly?

---

### Post by devnulljp on 2007-04-12
Are you using a proxy server for http? What sites are slow? Always the same ones?(maybe they're just slow?) Are they javascript/java/jsp/php pages?

---

### Post by NaCl on 2007-04-12
> **tipsqueal said:**
> Do you have another PC? If so, have you noticed the same or similar problems on it? Do you have any network hardware, for example routers, switches, hubs, network card, etc.? If so have you checked to make sure they are all connected/installed/configured correctly?

No, I don't have another PC/hardware. I am directed connected to an ethernet jack on campus. I just let ubuntu configre my computer upon installation. My roommate doesn't have problem going online on Windows.

---

### Post by NaCl on 2007-04-12
> **devnulljp said:**
> Are you using a proxy server for http? What sites are slow? Always the same ones?(maybe they're just slow?) Are they javascript/java/jsp/php pages?

All websites don't work when that problem occurs.

---

### Post by RomeReactor on 2007-04-12
Hi. It may be an IPv6 problem; if you're using Firefox, enter **about:config** in the address bar. Then search for **IPV6** and when **network.dns.disableIPv6** appears, toggle it to **true**. Now restart Firefox and see if you can browse the pages faster. If you don't use Firefox, you can disable IPv6 in your system by opening a terminal and entering

```
gksudo gedit /etc/modprobe.d/aliases
```

Now look for an entry that reads **alias net-pf-10 ipv6** and comment it out (put a **#** at the start of that line, so the system disregards it), and below that line add **alias net-pf-10 off**, so it looks like this

```
#alias net-pf-10 ipv6
alias net-pf-10 off
```

Save and reboot.

---

