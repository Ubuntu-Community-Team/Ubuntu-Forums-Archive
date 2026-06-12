---
title: "Hi, small wireless networking issue."
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-07-09
Hi, I can't connect to any wireless networks on my laptop with built-in wireless.   On my PC, with the PCI wireless card, it was straightforward, automatic installation, no driver download necessary. But this one's different.

Can someone help me to get it to work? 

I'm using an intel 2915ABG wireless. I think I may need drivers, I tried to install the ipw2200 drivers, however I never managed to get it to work. Are there any binary drivers for this?

---

### Post by originald on 2007-07-09
Hi

Try this link as seems like someone had a similar problem but has solved it now

Check the links within this thread
[http://ubuntuforums.org/showthread.php?t=275478&highlight=intel+2915ABG+wireless]("http://ubuntuforums.org/showthread.php?t=275478&highlight=intel+2915ABG+wireless")

---

### Post by Neon_Knight on 2007-07-09
Hmm, there are alot of links, and alot to read through, but I don't think I can solve my problem there. It's somewhat too advanced, I think.   If there's a binary driver I can simply install with apt-get install, then that would be great but I don't know if there is, and I can't seem to find one in any of those links...

---

### Post by dstew on 2007-07-09
There are many reasons why a wireless card might not be working. First, is it detected? To find out, run the command **sudo lspci** from a terminal window. See if the card is in the list. Second, does it have a driver that is working with it. To find out, enter the command **sudo iwconfig** from a terminal window. It should show your card associated with an interface device name, like wlan0. Third, is it configured correctly? For this one, the usual problem is not entering the WEP or WPA key correctly in the Network configuration page.

---

### Post by lbelloq on 2007-07-09
That's a pretty nice resume of how to troubleshoot WiFi cards.

---

### Post by Neon_Knight on 2007-07-10
It's ok, I solved it.  

I had to turn it on from a small switch in the front.

---

