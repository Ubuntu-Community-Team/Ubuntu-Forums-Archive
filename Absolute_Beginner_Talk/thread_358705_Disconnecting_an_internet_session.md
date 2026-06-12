---
title: "Disconnecting an internet session"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by John E on 2007-02-11
My ISP (Tiscali) has a very occasional problem where I seem to log in correctly, but I'm not connected to the internet (in other words, my browser cannot navigate to any site). This happens under both Windows & Ubuntu so either it's a local hardware problem at my end or a problem with my ISP.

Under Windows, I can simply right-click on my internet connection icon (on the System Tray) then I disconnect and reconnect. Under Ubuntu, the only way I currently know of is to re-boot. Is there an easier way to disconnect an internet session and re-connect?

---

### Post by Daveth on 2007-02-11
is this a dial-up connection then, and not broadband/adsl i.e "always on"  ???

---

### Post by John E on 2007-02-11
Oops - I should have been more specific. It's a broadband connection using a USB ADSL modem.

---

### Post by argie on 2007-02-11
You might want to try using the network-admin:
System > Administration > Networking

Then select your connection there and press Deactivate and then wait a little and then Activate.

EDIT: Whoops, I just saw that previous post. I'm not sure if this will work there. I've only used dialup and ethernet.

---

### Post by John E on 2007-02-11
No, that doesn't seem to be applicable. There's no entry for my broadband modem - only one for my LAN connector another entry for an in-built dial-up modem which I never use any more. Is it possible to disconnect from within FireFox?

---

### Post by PurplePenguin on 2007-02-11
Isn't your DSL modem going through your lan card?  Wouldn't you just treat it as a direct lan connection?  That's what I do, although I've always been behind a router which might change things.

EDIT: That is, if you want to disconnect your broadband, just disconnect the lan connection.

EDIT 2: Could this be related to the fact that DSL modems are usually given dynamic IP addresses by ISPs?  That is, you'll connect, use the internet for a while, but then after some period of time, it won't work (because you got assigned a new IP address), when you reconnect, it fixes the connection?  As I mentioned, I'm connected to the net through a router, and I've got it set to keep the connection alive.  There might be a setting somewhere (one of the routerless guys might help you) that will monitor your connection and make sure that you're constantly connected (properly) to the net.

---

### Post by John E on 2007-02-11
No, PurplePenguin. I think this is a problem at my ISP's end. It doesn't tend to happen after a long time. It either happens as soon as I connect or it doesn't happen at all. My DSL modem is connected via USB, not ethernet.

---

