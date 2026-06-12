---
title: "Wireless on boot"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by atad6 on 2005-09-16
Hi,

I've been trying to figure out how to have my wireless set up and activate on boot. I've been searching but have not found out exactly how to do this. Any help would be greatly appreciated.

Thanks!

---

### Post by poofyhairguy on 2005-09-16
[QUOTE=atad6]Hi,

I've been trying to figure out how to have my wireless set up and activate on boot. I've been searching but have not found out exactly how to do this. Any help would be greatly appreciated.

Thanks![/QUOTE]

What wireless hardware do you have?

---

### Post by mlomker on 2005-09-16
It's configured in the /etc/network/interfaces file.  Put your config under the proper interface and then add **wlan0** or whatever your interface is called to the **auto** line.

If you post that file we could give it a gander.

---

