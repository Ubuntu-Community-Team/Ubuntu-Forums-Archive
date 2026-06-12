---
title: "Wireless Network"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by trav777 on 2006-08-01
I have loaded Ubuntu on my sisters laptop which has a wireless card, but it is unable to detect a network.  I have Ubuntu on my laptop also and I was able to log onto the wireless network easily.  Will I need to install the Windows drivers on my sisters laptop?  If so....how?

---

### Post by tehnad on 2006-08-01
Is it an internal wireless card or PCMCIA?  What kind of Laptop?

---

### Post by Cath0de on 2006-08-01
There's a great wireless tutorial over at: [https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Otherwise, I've been having lots of trouble with my wireless lately and if you provide some information on the outputs of lshw and ipconfig commands, I might be able to point you in the right direction. You might just need to install new drivers, relatively simple.

---

### Post by trav777 on 2006-08-01
It is an internal Wireless Card and the laptop is an HP.

Cath0de, what you just said, other than the bit about the turtorial made no sence to me lol.

---

### Post by Cath0de on 2006-08-01
ok, do this, :D :
```
sudo lshw -businfo
```

copy and paste the output.

And then this:

```
sudo lshw -C network
```

copy and paste the output

---

### Post by tehnad on 2006-08-01
Found this on Google.  Seems relivant to your issue.  Hope it helps
[http://www.redrockcomputer.com/zv5340_wireless.htm](http://www.redrockcomputer.com/zv5340_wireless.htm)

---

### Post by trav777 on 2006-08-01
Ok, fallowed the troubleshooting guide and found out that it does have the driver installed.  It's just taht it won't stay enabled.  I go to System > Administration > Networking and then Activate eth1, the wireless card.  Then I make it my default.  Click Ok and it takes about 3 minutes to close.  Go back and it's disabled again...

---

