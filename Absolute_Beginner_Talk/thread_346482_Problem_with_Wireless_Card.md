---
title: "Problem with Wireless Card"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by Freaky Linux on 2007-01-25
I need help with my wireless card on my Laptop. My laptop is a Dell Inspiron 600m running Ubuntu Linux 6.10 and i can't get my wireless card setup, Please Help!:confused: 

Wireless Card: Dell Wireless 1370 MiniPCI WLAN

---

### Post by rmartz on 2007-01-26
You can identify your wireless card with: 

sudo lspci -vv

entered in a terminal window.

It will give you a lot of info. You can scan through and find the type of wireless network adapter, then search the forums for instructions as to how to install the correct drivers.

Hope that helps a little.

---

