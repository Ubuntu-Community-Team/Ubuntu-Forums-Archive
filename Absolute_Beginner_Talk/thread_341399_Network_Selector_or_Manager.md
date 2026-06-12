---
title: "Network Selector or Manager"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-01-18
I have a laptop that I use on wireless networks at my house and one at school (the one at school requires us to log in through a browser as well).

Should I be using Network Manger or Network Selector under add/remove programs?

---

### Post by Pobega on 2007-01-18
Try Gnome's,> sudo aptitude install network-manager-gnome

---

### Post by brandoncolorado on 2007-01-18
Hey,

I got Network manager installed and it shows up in the bar.  The problem is that it says disconnected even though I am connected.  It says "no network connections available" but I am using my wireless connection to type here!

---

### Post by riven0 on 2007-01-18
If you're connecting to your school LAN, you may want to try installing wifi-radar:

> sudo apt-get install wifi-radar

---

### Post by Pobega on 2007-01-18
> **brandoncolorado said:**
> Hey,

I got Network manager installed and it shows up in the bar.  The problem is that it says disconnected even though I am connected.  It says "no network connections available" but I am using my wireless connection to type here!
Don't connect through System -> Networking; That always messed with my Network Manager settings too. Disconnect from that connection (Untick the wireless connection checkbox) and then restart network-manager-gnome; Should work like a charm.

---

### Post by l951b951 on 2007-01-18
Network Manager is the only way I was able to get my wireless working.  Couldn't get the command line to work for me, but Network Manager fixed it right up.

---

### Post by vigyani on 2007-02-16
Network Manager does not manage network interfaces configured manually, hence the confusion arises. The network interfaces you want to manage through Network Manager should not be configured manually. 
Hope this helps.
regards

---

