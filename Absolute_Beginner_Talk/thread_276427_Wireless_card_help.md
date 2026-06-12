---
title: "Wireless card help"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by NinjaJoey23 on 2006-10-12
Hi,

I am completely new to linux and have just installed ubuntu.

The problem I am having is with my wireless card. It is a Zonet ZEW1602, if I am not mistaken. I have been sifting through the wireless documentation, and have found stuff on ZEW1601, but not 1602.

The card appears in the device manager, but the option for wireless networking does not show up in the admin network list, just ethernet. As I do not have access to an ethernet connection, this is a problem for me :( 

I need some help finding a driver(?) and specifying it to the device. As I said, I'm very new, and honestly pretty lost.

---

### Post by FizDev on 2006-10-12
You could try installing your drivers with ndiswrapper. It uses the Windows drivers of your card. Follow these instructions :
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

(not sure if it works with your card)

---

### Post by NinjaJoey23 on 2006-10-13
I tried to use ndiswrapper and I froze my system to the point that I had to reinstall ubuntu. It's been a rough first day.

Anymore advice for this? I want to stay with ubuntu, but I have to have internet for that to be reasonable.

---

### Post by Foudre on 2006-10-13
dumb question, i bet  you already did, but under networking did you enable the wireless device, rather then just looking for the networks?

---

### Post by NinjaJoey23 on 2006-10-13
The device (ie my wireless card) doesn't show up under the networking area. The ethernet does, but not the card. Now, the card does show up in my device manager list, but I don't have the right driver.

---

