---
title: "[SOLVED] How to use Wireless network"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by LinuxIsInnovation on 2007-12-29
I have Intel 3945ABG 802.11 a/b/g WLan on my laptop. The driver comes in the list of restricted drivers. Reading other posts, I found that installing network-manager would enable WiFi and I would see a signal icon in the tray area. But network-manager is already installed in Gutsy. So how do I use my Wireless adapter?

---

### Post by shanepardue on 2007-12-29
If you left-click the network-manager applet, it should list the wireless networks in your area.

---

### Post by LinuxIsInnovation on 2007-12-30
I get an option to Connect to a wireless network and to create a new wireless network
When I click on either, the Network-manager icon disappears :o

---

### Post by shanepardue on 2007-12-30
> **sayakb said:**
> I get an option to Connect to a wireless network and to create a new wireless network
When I click on either, the Network-manager icon disappears :o
Try opening network-manager with this command in the terminal "nm-applet". When it 
errors, it should display something in the terminal you opened it with. If you don't know 
what the error message means, paste it here and we'll give it a shot.

---

### Post by LinuxIsInnovation on 2007-12-30
*Wink wink* Its fixed!! I reinstalled network-manager and now its working.
Thanks for replying :D

---

