---
title: "I can't access network settings."
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Tha_Pig on 2007-12-18
I'm using Xubuntu on a Ramline tablet.

My computer recognized the wireless network card (Belkin) but it could not connect to the wireless network. I tried to change some of the network properties and restarted the computer.

Now I can't open the network properties at all. I click the menu icon and I get the clock cursor for a few seconds... then nothing. I tried both with or without the network card in the slot with the same result.

Is there another way to change the network settings, or reset it to default?

I would appreciate any help.

---

### Post by Evil_Catbert on 2007-12-18
Open a terminal
Go to the folder /etc/network
type ```
cd /etc/network 
```
open the file "interfaces" as superuser
```
sudo nano interfaces
```

The "interfaces" file contains your network settings

---

### Post by Tha_Pig on 2007-12-20
I get this message:

**sudo: unable to lookup (none) via gethostbyname( )**

---

