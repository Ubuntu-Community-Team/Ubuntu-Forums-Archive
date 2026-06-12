---
title: "Optus 3G wireless internet"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Mindless1 on 2008-02-22
Has anyone used the optus wireless internet. You get a small modem which connects to your computer via USB.

I cant seem to get it to work, you insert a sim card into modem and it is supposed to connect to the network.

Does anyone have any ideas?

---

### Post by kristjans on 2008-02-22
Chances are low that any other Linux user that uses Optus 3G stumbles on this thread anytime soon. However, to get you started, I found this on Google:
[http://freshfoo.com/wiki/Using_Optus_3G_with_Linux](http://freshfoo.com/wiki/Using_Optus_3G_with_Linux)

If not anything else, it should get you started.

---

### Post by ubuntulinesman on 2008-07-23
I tried the instructions at
[http://freshfoo.com/wiki/Using_Optus_3G_with_Linux](http://freshfoo.com/wiki/Using_Optus_3G_with_Linux)
and they worked except for one line which I left out. The line I left out is
OK "AT_OPSYS=1"

My question is, is there a GUI that can be used to connect and shows the usage stats or is there a way to use the Windows GUI?

Thanks,
ubuntulinesman

---

### Post by Sealbhach on 2008-07-23
Yes, I have used Gnome-PPP for my 3G modem.

```
sudo apt-get install gnome-ppp
```

There's also a KPP if you're using KDE.


.

---

### Post by ubuntulinesman on 2008-07-23
Vodafone have a GUI for connecting their USB modem which is the same as the Optus modem. I wonder if the Vodafone can be re-configured for the Optus card. Any ideas??

---

### Post by ubuntulinesman on 2008-07-23
I just installed the Gnome PPP but haven't configured it yet. It looks very promising, thank you.

---

