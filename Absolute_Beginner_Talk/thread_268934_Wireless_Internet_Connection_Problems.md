---
title: "Wireless Internet Connection Problems"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Nut on 2006-09-30
Okay, this is my problem, I have no idea what to do to setup my **external USB network adapter**. Could somebody just type out a list of steps on what to do? I would greatly appreciate it.

**Here's an example of what I want the list of steps to look like so it can help me:**

1. Open the terminal and type "sjncdjcnmsdc".
2. Click this and open the network tools.

Thanks in advance!

---

### Post by blx_286 on 2006-09-30
> **Nut said:**
> Okay, this is my problem, I have no idea what to do to setup my **external USB network adapter**. Could somebody just type out a list of steps on what to do? I would greatly appreciate it.

**Here's an example of what I want the list of steps to look like so it can help me:**

1. Open the terminal and type "sjncdjcnmsdc".
2. Click this and open the network tools.

Thanks in advance!

I think part of that will depend on the card you have. Do you have any details on your card?

---

### Post by Nut on 2006-09-30
I have a Model WUSB546 Version 4 Linksys G-Wireless USB Network Adapter

---

### Post by theratster on 2006-10-01
I have a similar adapter, but mine is actually a D-LINK.

I just had it plugged in, and booted up into Ubuntu. Then just go to Network tools. It *should* be listed under "Wireless". (In my case it was called rausb0). Then click properties, click "activate" then type in the name of the router, the password, select DHCP, and click OK. Then click Activate. It should work now!

---

### Post by Nut on 2006-10-01
I did that but my router doesn't have a password (WEP Key) so I didn't enter one...

It didn't work.

---

### Post by blx_286 on 2006-10-01
> **Nut said:**
> I have a Model WUSB546 Version 4 Linksys G-Wireless USB Network Adapter

Maybe this will get you going in the right direction [http://ubuntuforums.org/showthread.php?t=192588&highlight=rt2500]("http://ubuntuforums.org/showthread.php?t=192588&highlight=rt2500")

This wiki shows that your card is using the rt2500 drivers [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53")

This wiki has general wifi stuff and a link for the rt2500 drivers [http://https://help.ubuntu.com/community/WifiDocs]("http://https://help.ubuntu.com/community/WifiDocs")

This wiki has further info on the RalinkRT2500 driver [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28WifiDocs%2FDriver%29]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28WifiDocs%2FDriver%29")

But, it looks like the first link would probably get you going. The guy put a lot into documenting the installation. Hope that helps. If it does, you may want to save a local copy of that thread or print it out, just in case you need it again.

---

### Post by Nut on 2006-10-01
Dude, I don't even know what they're telling me there.

Somebody's got to speak retard to me here.

---

### Post by Frak on 2006-10-01
Be sure to change lo to wlan0 in network connections.
(I have the same model you do)

---

### Post by Nut on 2006-10-01
Still having problems.

Help!

---

