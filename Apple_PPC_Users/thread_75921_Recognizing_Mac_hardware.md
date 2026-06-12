---
title: "Recognizing Mac hardware"
date: 2005-10-14
forum: Apple PPC Users
---

### Post by Benboom on 2005-10-14
Hi;

I've just installed 5.04 on a mac G4 Sawtooth (AGP graphics, OS 9.2.2). Ubuntu runs fine but I have problems accessing the outside world. This machine has only an internal modem and that's the only way I can connect to the internet so I can't figure out how to use the software update stuff at all. Is it possible to get the system to recognize the modem?

Also, can Ubuntu be configured to see my internal ZIP drive? It would sure make moving stuff between machines easier.

Thanks very much.

---

### Post by ristosu on 2005-11-08
I don't dare to say anything about the modem, I don't even have experience of the machine, only its predecessors, but there should be no reason for not being able to access the zip-drive. It's probably hanging on an ide-bus. So it should exist as one of /dev/hda, /dev/hdb, /dev/hdc, etc. As far as I know the device-entries are created on-the-fly while the drives are recognized.

---

