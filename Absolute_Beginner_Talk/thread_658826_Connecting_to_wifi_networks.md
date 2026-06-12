---
title: "Connecting to wifi networks?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Avant Gardener on 2008-01-05
I have a fresh Compaq c581WM Laptop. The network card is an "Integrated 10/100 Ethernet LAN"

I would really like to convert my laptop to Ubuntu 7.10 (from Vista).

However, I can't connect to my wireless network that's on a Belkin 54 WirelessG Router. If I can't connect to wireless networks easliy, and access the internet, I might as well not have a computer (almost all of my computing tasks involve the web or downloading applications, documents, etc.)

My first question is then: Is it necessary to INSTALL Ubuntu before I can connect to my network?

My second question: How do I connect/detect the network?

My last question: If I roam around a lot (cafes, school, etc?) how do I connect/detect various other networks?

---

### Post by zipperback on 2008-01-05
> **Avant Gardener said:**
> I have a fresh Compaq c581WM Laptop. The network card is an "Integrated 10/100 Ethernet LAN"


the "Integrated 10/100 Ethernet LAN"  is the standard NIC. 

What kind of wifi adapter does your laptop have in it?

Please post the output of the following:

ifconfig

iwconfig

lspci

Thank you
- zipperback
:popcorn:

---

### Post by lisati on 2008-01-05
> **Avant Gardener said:**
> I have a fresh Compaq c581WM Laptop. The network card is an "Integrated 10/100 Ethernet LAN"

I would really like to convert my laptop to Ubuntu 7.10 (from Vista).

However, I can't connect to my wireless network that's on a Belkin 54 WirelessG Router. If I can't connect to wireless networks easliy, and access the internet, I might as well not have a computer (almost all of my computing tasks involve the web or downloading applications, documents, etc.)

My first question is then: Is it necessary to INSTALL Ubuntu before I can connect to my network?

My second question: How do I connect/detect the network?

My last question: If I roam around a lot (cafes, school, etc?) how do I connect/detect various other networks?

1. If you have a copy of the "Live CD", you will be able to have a play to see if you can connect to a network (either wired or WiFi) before you install. 

2. There will be an icon at the top right of the screen which you can click on to control your connection.

---

### Post by Avant Gardener on 2008-01-05
I have a "Broadcom 802.11b/g WLAN" adapter and a "Realtek RTL8139/810x Family Fast Ethernet NIC"

I have the LiveCD and tried connecting, but didn't understand much....i.e. the:

ifconfig

iwconfig

lspci

P.s. Thanks for the promptness...

---

### Post by lisati on 2008-01-05
> **Avant Gardener said:**
> I have a "Broadcom 802.11b/g WLAN" adapter and a "Realtek RTL8139/810x Family Fast Ethernet NIC"

I have the LiveCD and tried connecting, but didn't understand much....i.e. the:

ifconfig

iwconfig

lspci

P.s. Thanks for the promptness...

The "ifconfig" and other stuff are commands that let you discover something about your PC's networking capabilities and settings that might be useful for asking questions. Within Ubuntu, you'll need to open up a terminal window (the equivalent of a "DOS box" or "command console" in Windows). You can find it on the Applications->Accessories menu.

---

