---
title: "Installer Becomes Unresponsive"
date: 2010-03-25
forum: Apple Hardware Users
---

### Post by penguirl on 2010-03-25
I have installed and run Ubuntu on my iMac, now I would like to try Kubuntu but the installer hangs every time inbetween step 1 setting language and step 2 choosing time zone. Sometimes it's while the system clock is being set, sometimes after. It's just the installer that is locked up, I can still move the cursor but because the installer is fullscreen I cannot get out of it, at least not that I know of.

I have made two different desktop CDs from two different ISOs and both gave the same exact behaviour. I think I prefer Kubuntu to Ubuntu but I haven't really been able to give it a try.

---

### Post by linuxopjemac on 2010-03-25
you can also just install ubuntu and then install the kubuntu-desktop. Once you are in KDE, you remove the ubuntu-desktop.

---

### Post by penguirl on 2010-03-25
Thanks, I went ahead and installed KDE but I wasn't sure about deleting Gnome. No rush I guess, I'm just test driving them both and waiting to see what Lucid brings.

---

### Post by penguirl on 2010-03-25
Turns out it's not as simple as just deleting all Gnome/Ubuntu packages, you have to be very selective if you want your computer to remain functional. I wish I could just install Kubuntu to start with, if for no other reason than to be able to do a comparison of package installs so I would know for sure what I do not need.

---

### Post by linuxopjemac on 2010-03-25
I think a 

```
sudo apt-get install kubuntu-desktop
```

and

```
sudo apt-get remove ubuntu-desktop
```

will do the job

---

### Post by penguirl on 2010-03-26
That makes perfect sense, I should've asked in the first place. Oh well at least next time I'll know, thank you.

---

### Post by SushiR on 2010-03-27
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

