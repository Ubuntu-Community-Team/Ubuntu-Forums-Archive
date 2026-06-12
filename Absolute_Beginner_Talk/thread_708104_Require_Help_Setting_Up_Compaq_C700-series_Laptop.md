---
title: "Require Help Setting Up Compaq C700-series Laptop"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Grimhound on 2008-02-26
I just had Windows utterly flake on me, so I'm attempting to get Ubuntu up and running on my Compaq Presario C700 series laptop. Yet I'm running into some difficulty when it comes to setting up the Wireless on it. My Wireless, managed apparently by a card of the Broadcom 43xx chipset family, says that it is managed by proprietary firmware, and I need help in figuring out how to fix it so I'm able to access my wireless on the laptop. Anyone able to help?

When I try to enable it, it sends up a popup stating this:

The software source for the package
bcm43xx-fwcutter
is not enabled.

---

### Post by agim on 2008-02-26
This may help
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

If not, post your network card by using this command

lspci

paste the output of that command here

Edit: In fact, just post lspci first.

---

### Post by Grimhound on 2008-02-26
Alright. I did that. Now how do I get the internet to actual work? It still isn't letting me onto the network.

Is there a way to browse for wireless networks?

---

### Post by Grimhound on 2008-02-26
-

---

### Post by Grimhound on 2008-02-26
Would this be what you needed to see?

1:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

---

### Post by Grimhound on 2008-02-26
Well, I need to head off. If anyone has any idea what I need to do to get the wifi working, please help.  Really need to get that laptop connected. @.@

---

### Post by Deanodriver on 2008-04-05
I have a C700 (it's a C731TU with an Atheros wifi chipset, though), and the instructions on the Wiki meant for the Asus EeePC helped get this wireless working.

Have you tried using ndiswrapper? (I'm a newbie to wireless, unfortunately)

---

