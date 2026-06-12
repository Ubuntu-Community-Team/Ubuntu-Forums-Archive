---
title: "how do i turn on wireless card"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Andrew79 on 2008-02-17
just booted ubuntu and a newb to this, from windows. when i connect the ethernet cable, internet works fine. then when i disconnnect, i can not find, or make work a wireless connection. will not see a access point five feet away. says card is off, how do i turn it on?

---

### Post by amohanty on 2008-02-17
By default, you need to check if you see the network icon in you systray (the tray in the panel at the top right corner by default). It should show you a netwrok broken icon. 

Now if you click on it, do you see the SSID of your access point? If you set upt your AP in hidden mode, you will not see it and will have to manually set it up by selecting "Connect to other wireless network" when you click on the applet in the tray.

If you manually mucked with your /etc/network/interfaces nm-applet (the one I mentioned above) will nto work, you will need to comment out some lines. 

Finally, what laptop is this? Do you know what kind of wireless card it has on?

AM

---

### Post by Presto123 on 2008-02-17
Connect your computer with your cable, then go into System/Administration/Restricted Drivers Manager and if the card shows up as available, click on the box to enable it. It will pop up with a new window asking you where to get the driver. Select the second option to download from the internet. It SHOULD work then.

---

### Post by Andrew79 on 2008-02-17
BCM94311MCG wlan mini-PCI
 Broadcom Corporation
this is the card, it says it is acctually turned off, the network works fine with the windows computers sitting on the same desk

---

### Post by Presto123 on 2008-02-17
*Edit* I missed some stuff.

Try amohandy's tip.

---

### Post by kamaboko on 2008-02-17
You could start by showing it some sexy pictures, but that depends on what you mean by turning it on. :)

---

### Post by voteforpedro36 on 2008-02-17
> **kamaboko said:**
> You could start by showing it some sexy pictures, but that depends on what you mean by turning it on. :)

:) I lol'd

Either way... that card *should* be under the Restricted Drivers Manager, so connect and download if so... And make sure it's on, as in PRESS THE BUTTON on the side of the computer if you must (speaking from experience there).

---

