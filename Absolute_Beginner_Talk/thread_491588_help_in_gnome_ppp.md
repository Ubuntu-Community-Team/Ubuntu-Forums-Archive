---
title: "help in gnome ppp???"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by nooor7772000 on 2007-07-03
help in gnome ppp??? 

--------------------------------------------------------------------------------
[SIZE="4"]
hi i try conect to usb modem by nokia 6630 in ubuntu and it work well in windows well by these setting,,,,,,,,how can i apply these setting specilly the bold written in gnome ppp well to make it work ......i want apply all these setting to get it work as nothing from previous posts help me in..............[/SIZE]


Configure the Modem:

- Choose 115200 from the Maximum Port Speed drop-down menu
- Select Advanced tab, enter the following into the Extra initialization commands field: **AT+CGDCONT=1,"IP","MOBINILWEB"**- Select Change Default Preferences and **change the Flow Control field to read None**

Dial-up Networking Set-up:
- Enter the relevant telephone number:
***99# **for most GPRS handsets

- From the Modem Configuration select 115200 as the maximum speed (bps)
[B]- Tick Enable hardware flow control
- Un-tick Enable modem error control
- Un-tick Enable modem compression
- Un-tick Enable modem speaker[/B]
-
**- Un-tick Use dialing rules.**

- **Untick Use IP Header compression**

---

