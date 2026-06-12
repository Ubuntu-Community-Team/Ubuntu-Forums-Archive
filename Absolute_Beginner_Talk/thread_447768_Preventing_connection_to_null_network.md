---
title: "Preventing connection to null network"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by AlanD on 2007-05-18
Occasionally, I will lose my wifi connection, and Feisty will try to reconnect. However, occasionally, it will try and connect to a wifi network called "null", which in turn crashes Linux. I don't know if this is a bug or not nor do I know how to report it, so I'm posting it here :) Is there any way I can stop it from trying to connect to a null network?

Using a Broadcom 43xx type wifi card (used bmc43xx-fwcutter) in a Lenovo 3000 C100, on regular Ubuntu with latest updates.

---

### Post by Najand on 2007-05-18
Are you using the new feature in Feisty with Roaming Mode?
If you want to connect it to just one Wireless network you can set it up at 
System -> Administration ->  Network
Select your Wireless Connection and then:
Uncheck Roaming Mode and enter your wireless network information.

---

### Post by AlanD on 2007-05-18
I am using Feisty with roaming mode, but I don't want to be limited to just this wifi network (it is my school's).  I just want it to stop freezing when it drops a connection and tries to reconnect to this "null network" :<

---

