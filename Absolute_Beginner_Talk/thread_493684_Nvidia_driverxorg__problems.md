---
title: "Nvidia driver/xorg  problems"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by alex132 on 2007-07-06
I installed ubuntu on one computer without problems. When i try to install it on a newer computer, i am running into problems with the nvidia drivers/xorg configuration. I change settings in the nvidia driver dialog with sudo privilages and when i save to xorg.conf everything seems to be working well. After i reset the x server or the system i get a text display error asking to re-configure my displays. I try going through the process but nothing seems to work. i am on a geforce 6600 with two crt monitors. Anyone know how i can fix this?

---

### Post by zero244 on 2007-07-06
Could you show a copy of your xorg.conf

---

### Post by aquavitae on 2007-07-06
> **alex132 said:**
> I change settings in the nvidia driver dialog with sudo privilages and when i save to xorg.conf everything seems to be working well. 
What exactyl did you change?  Can you post the contents of xorg.conf.
> 
After i reset the x server or the system i get a text display error asking to re-configure my displays.
By text display message do you mean from the console, i.e. the xserver won't start?  If so, can you post the output of 
tail -20 /var/log/Xorg.0.log

---

