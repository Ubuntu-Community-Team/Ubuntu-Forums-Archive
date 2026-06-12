---
title: "Alternatives to 'Network Manager'"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2007-06-28
What are some alternatives to 'Network Manager'?  I need something to manage my Wi-Fi connection as 'Network Manager' doesn't seem to like WPA encryption and even now that I have configured my router for WEP encryption, I still can't get in.

---

### Post by bedfojo on 2007-06-28
Try wicd. See [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Works for me.

---

### Post by mikewhatever on 2007-06-28
In my case, the network manager did not work with WEP too, but when I edited /etc/network/interfaces, putting in the network name and WEP, all was fine. Here is what it looks like, the relevant part:> iface eth1 inet dhcp
wireless-essid Network_Name
wireless-key s:WEP_KEY

If I want to use the network manager, which is very rare, I'd comment out the last two lines. Not quite what you are looking for, but works.

---

### Post by a13kurt on 2007-06-28
I'm having the same problem with WEP and my chosen network manager.  I've tried to change the interface file in the etc/network directory, but when I try to save my changes it won't allow me due to permissions.  How do I fix my current situation? Further directions or an alternative program (I've already tried wicd and it wouldn't work) would be greatly appreciated.

---

### Post by mikewhatever on 2007-06-29
To edit the interfaces file, go to System>Administration>Network, choose the wireless and click properties, insert the relevant information and reboot.

---

### Post by a13kurt on 2007-06-30
I tried your advice and my results are as follows: With WEP 128 enabled on my router and WEP disabled on my pc I received no signal.  With the WEP key on both my pc and router, my pc said I had a signal, but wouldn't receive an IP address. Any other ideas?

---

### Post by motin on 2008-03-01
> **mikewhatever said:**
> To edit the interfaces file, go to System>Administration>Network, choose the wireless and click properties, insert the relevant information and reboot.

No need to reboot. Instead, run:
```
sudo /etc/init.d/networking restart
```

---

### Post by motin on 2008-03-01
> **bedfojo said:**
> Try wicd. See [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Works for me.

Btw i second this too. Wicd works ten times better for me than NetworkManager. Got my AdHoc wireless network running in 30 seconds - something I have been struggling with for weeks!

---

