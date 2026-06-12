---
title: "[SOLVED] pppoeconf Internet Connection Problems"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by h4l0 on 2007-12-12
I have just bought a Dell Inspiron 6400 Notebook, ditched vista and installed Ubuntu 7.10.  I have D-Link DSL 502T ADSL ROUTER/MODEM.

When I follow the instructions at [https://help.ubuntu.com/7.10/internet/C/modems-adsl-pppoe.html](https://help.ubuntu.com/7.10/internet/C/modems-adsl-pppoe.html) Step 1 finds eth0.  

However, Steps 2 and 3 say I should be prompted fo a Username and Password.  This doesn't happen and pppoeconf scans eth0 for a Concentrator and returns the following error:

"Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the failure may also be another running pppoe process which controls the modem."

I ran ps and no other pppoeconf process is running.  I can access my DSL 502T on 10.1.1.1 and login as admin.

Any ideas?

Thanks

---

### Post by cmnorton on 2007-12-12
What are the contents of /etc/network/interfaces?

As of 7.10, mine looks like this:

auto lo
iface lo inet loopback

Is your network connection open or WEP-encrypted. I have WEP-encryption and got all hung up when I specified the password type. It had to be 64/128 HEX (if you're giving an already translated passphrase). In addition I needed to choose that the connection was passphrase and not open. 

D-Links have that nice feature that takes your ASCII passphrase and translates into one or more HEX strings.

Are you using a built-in card? I had problems with my Acer Travelmate 630's built-in card.

---

### Post by h4l0 on 2007-12-13
I re-installed Ubuntu 7.10 and it works now.  I have no idea what fixed the problem.  I have learned a little about connecting to the internet.

Thanks for the reply.

Nick:guitar::guitar:

---

