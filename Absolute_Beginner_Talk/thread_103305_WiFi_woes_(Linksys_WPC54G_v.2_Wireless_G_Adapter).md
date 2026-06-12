---
title: "WiFi woes (Linksys WPC54G v.2 Wireless G Adapter)"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by swregulator on 2005-12-13
I have gone through several threads, using ndiswrapper to install the driver, configuring network settings as described, etc., and I cannot make a wifi connection between my laptop and wireless router (also a Linksys).  It used to work when I had XP on the laptop.  An ethernet connection between the laptop and the router works fine.  The problem is that the laptop never powers up the Wireless G adapter.  The green lights on the adapter never come on.

I'm ready to give up, as I've spent hours going through the threads.  I'm open to last-gasp suggestions.

---

### Post by Kurt Dodrill on 2005-12-14
Have you tried the Linuxant drivers?

---

### Post by swregulator on 2005-12-14
No.  What are they, and where can I find them?  Have others used them with this Adapter and had success?

---

### Post by Gamabunta on 2005-12-23
I believe you have to pay for those drivers...so don't use them.

If your green lights don't come on at all, it may be your laptop's cardbus interface that is the problem. Insert your card in another laptop and see if the power light goes on.

Anyway, this is how I got the WPC54G to work on my laptop:

1. Install ndiswrapper-utils and ndisgtk (from universe) in synaptic
2. Make sure you get a new menu item - system>admin>Windows Wireless Drivers
3. Put in your card
4. Put in the wireless card driver installation CD
5. Goto Drivers>NT and copy the .inf file to your home folder
6. Open Windows Wireless Drivers
7. Install the .inf file, then configure your network
8. A new wireless option should appear
9. Enter in your wireless settings via 'properties'
10. Activate the card, restart, enjoy

---

