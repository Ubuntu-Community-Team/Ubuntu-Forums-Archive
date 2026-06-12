---
title: "Lost wireless connection"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by zumbi77 on 2006-09-28
Hi

Installed Dapper on my Dell latitude d600 with a broadcom 4306 card. After a bit of hazzle I got the wireless working. That is, until yesterday.

First I tried to connect at a café. Couldn't get it to work. When I got back home I tried again, but no connection. Opening the network utility (my translation, not sure what it is called in english)it seems like the computer no longer detects my wireless card. It used to be there, but now i can only see the ethernet and modem connection.

Any suggestions on how I can solve my problem will be appreciated.

Andreas

---

### Post by Kateikyoushi on 2006-09-28
I hope [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper") helps.

---

### Post by zumbi77 on 2006-09-28
Thanks. Seems like I found the solution in the guide. Typed:

sudo iwconfig wlan0 rate 11M

No idea what I just did, but it worked.

---

