---
title: "this is weird..."
date: 2007-08-28
forum: Apple Intel Users
---

### Post by ziofil on 2007-08-28
hi everybody, i managed to install feisty on my macbook pro c2d, it works perfectly but... not the wireless card.
it seems strange, i followed almost all the how-tos i found, but the system still doesn't see the ath0 device...
if i try ```
ifconfig ath0 up
``` i get ```
ath0: ERROR while getting interface flags: No such device
```
but if i try ```
lspci | grep Atheros
``` i get ```
03:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
```
:confused:

I installed madwifi drivers and everything but as you can see nothing good happens..!
any suggestion?
thank you in advance
Ziofil

ps sorry if i started a new thread, but i didn't find anybody with the same problem.

---

### Post by ziofil on 2007-08-28
solved!!

[http://madwifi.org/ticket/1001#comment:179]("http://madwifi.org/ticket/1001#comment:179")

:guitar:

---

