---
title: "Can't connect to dial-up internet"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-03-29
How do I connect to the internet using prepaid dial-up internet card?

I'm trying to connect using KPPP configuration but I can't make it work. I can't add a login ID and password after adding an account for some reason.

I also tried gnome's network settings. I edited the modem connection. I enabled it, added a phone number, put a username and password, I also ticked the choices "set modem as default route to internet" and "retry if the connection breaks or fails to start," and chose /dev/modem as the modem port.

Have I done anything wrong? What should I do?

---

### Post by antmenj on 2007-03-29
Do you have a win modem or an external modem pluged into a com port?

I got my external modem going OK in the end with pppconfig

Open the terminal and type

> sudo pppconfig

Fill in the dial number, com port, user name, password, do NOT change the connection name from the default.  Save and exit.

In the terminal type pon to dial and poff to hang up.  You can make desk top icons to do that by right clicking the desk top and doing something... (can't remember at present - am using a win95B machine :oops:)

I tryed vwdial with no joy :(

---

### Post by unisol on 2007-03-29
try running sudo wvdialconf /etc/wvdisl.conf. if it detects your modem it should tell you what port it is on, provided its not a winmodem.

---

### Post by unisol on 2007-03-29
excuse my spelling its sudo wvdialconf /etc/wvdial.conf.

---

