---
title: "I have a question about wireless..."
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by dittyman1 on 2006-08-22
So, like many others, I'm having a little trouble setting up my Ubuntu machine's wireless internet access.  Ubuntu recognized my card, so that's fine.  But, I need to know the MAC address of my pc. I found instructions at wikihow for doing it in Windows, but there are no such instructions for linux.  Can anyone help?  Am I an idiot?  Thanks in advance.

---

### Post by neonhomer on 2006-08-22
If you have a built in Wifi, there is usually a label with the MAC address on the bottom of the machine on on the PCMCIA card.. if it's a laptop...

Otherwise, it would be on your card or on the box the card came in.

---

### Post by NetworkGuy on 2006-08-22
If the card is recognized, you might be able to do a ifconfig and get the MAC address.

---

### Post by dittyman1 on 2006-08-22
> **neonhomer said:**
> If you have a built in Wifi, there is usually a label with the MAC address on the bottom of the machine on on the PCMCIA card.. if it's a laptop...

Otherwise, it would be on your card or on the box the card came in.

Sorry.  I don't have a laptop.  I put a wireless card into a desktop.

---

### Post by dittyman1 on 2006-08-22
> **NetworkGuy said:**
> If the card is recognized, you might be able to do a ifconfig and get the MAC address.

"iconfig" would be using the command line, right?

---

### Post by NetworkGuy on 2006-08-22
Try ```
ifconfig
```

---

