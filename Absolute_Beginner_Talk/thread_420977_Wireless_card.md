---
title: "Wireless card"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by jpboyes on 2007-04-24
I just put ubuntu on my Gateway MX6960 laptop. I cannot figure out how to get my wireless card to work. I've tried installing the driver provided by intel (I have a 3945ABG wireless card), but when i go to install it, i get a message that i haven't installed the ieee80211 subsystem. I have installed that to the best of my knowledge, so i can't figure out what i am supposed to do. Please help...

---

### Post by Bachstelze on 2007-04-24
Those drivers have always been problematic in Ubuntu... Which release are you running ?

---

### Post by jpboyes on 2007-04-24
7.04 Fiesty Fox.

---

### Post by compmodder26 on 2007-04-24
That should be working out of the box in Feisty.  I have the same card and it has worked out of the box since Dapper.  In the top right corner you should see an icon that looks like two monitors.  Left click that icon and you should get a list of available wireless networks.  If the one you want to connect to is hidden, you'll need to manually configure it.  To do that, click "Create New Wireless Network".

---

### Post by jpboyes on 2007-04-25
It did that at first, but it was never able to connect. Eventually, that just stopped appearing. Now, the only things i see when i left click that are "wired network" and "Manual configuration". There is no option inside "Manual configuration to connect to a wireless network.

---

### Post by compmodder26 on 2007-04-25
I suspect you attempt at installing another driver may have hosed the existing one.  Unfortunately I'm not sure what your next step would be, besides a reinstall.  Perhaps try this command in a terminal:
```
sudo modprobe ipw3945
```

---

### Post by jpboyes on 2007-04-26
after you said that it should run natively, i decided since i had just installed it and the only other things that i had put on my computer since then were in an attempt to get that card working. I just decided to reinstall. Now it works fine. Thanks for all of your help.

---

### Post by compmodder26 on 2007-04-26
Glad it is working for you.

---

