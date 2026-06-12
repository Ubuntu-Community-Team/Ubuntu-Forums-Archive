---
title: "Need Help Setting Up Compaq Presario C700 Laptop."
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Grimhound on 2008-02-26
I'm trying to set up Gutsy on a Compaq Presario C700 series laptop, and am brand new to Linux. I keep running into issues.

One: Even after using the method of installing the bcm34xx-fwcutter, the Broadcom wireless card won't pick anything up.

Two: When I try to check anything via sudo and it asks for a password, Ubuntu locks me out of my own keyboard so I can't enter the password.

Three: I've had a few freezeups as I've been trying to get the Wifi card to pick up the internet.

Now, I'm at the point where it says the card is active, but I can't figure out how to get it to find the Wireless network. Does anyone have any tips or ideas or solutions so I can get my laptop up and running? I really would like to attempt to get Linux running first before I spitefully put Windows back on the drive. I'd really prefer not to lose my backup data /again/.

---

### Post by Iehova on 2008-02-26
Hi there, welcome to Ubuntu and Linux. :)

When you talk about Ubuntu 'locking you out of your keyboard' when you use sudo, are you sure you're not getting caught out by [this oddity?](http://www.psychocats.net/ubuntu/passwordinterminal)

I don't have a broadcom card, so I can't be much help, but if it is active and working the usual way to connect is with the network-manager applet in the top panel, it should appear like two computers near the top right. If you click that and see a drop-down list of wireless networks, you can connect by clicking the relevant one.

If nothing appears, right click it and see if "enable wireless" and "enable networking" are checked. If that doesn't solve your problems, you can left click on the applet again and hit "manual configuration". The first thing to check is if a wireless device is recognized. If so click it and hit "properties" and make sure "enable roaming mode" is checked. You can then try the network-manager applet again.

If that doesn't solve your problem then I'm sorry but I really can't help any further. ;)

---

