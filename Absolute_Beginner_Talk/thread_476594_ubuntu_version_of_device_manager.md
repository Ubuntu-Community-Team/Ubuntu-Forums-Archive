---
title: "ubuntu version of device manager"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by fast eddie on 2007-06-17
I am trying to set up wake on lan so that my squeezebox can start up my pc when I press the power button on the SB remote.

I had this working in XP but since I have changed to ubuntu I cant seem to get it to work. I had to set the wake on lan magic packet setting on my network card via the device manager in XP but I cant seem to find the corresponding setting in ubuntu. Am I correct in saying that I look in hardware system / preferences / hardware information?

The device (I think) is 82562EZ 10/100 Ethernet Controller. I cannot see any settings for wake on lan in the bios but my motherboard supports it because it worked when I was running XP.

Any help greatly received

---

### Post by w4ett on 2007-06-17
The short answer about the Hardware Manager is yes...but your Network controller can be accessed by System>Administration>Network

---

### Post by sailor2001 on 2007-06-17
in synaptics:  wakeonlan

---

### Post by fast eddie on 2007-06-17
Thanks for th reply but I cant see a setting where I can set the wake on lan magic packet.

Any ideas where this would be?

---

### Post by fast eddie on 2007-06-17
> **sailor2001 said:**
> in synaptics:  wakeonlan

Forgive my stupidness but I have installed this and not sure what I do next. I am new to linux so please bear with me.

Thanks for the help

---

### Post by nrwilk on 2007-06-19
> **fast eddie said:**
> Forgive my stupidness but I have installed this and not sure what I do next. I am new to linux so please bear with me.

Thanks for the help

Here's the homepage for wakeonlan:
[http://gsd.di.uminho.pt/jpo/software/wakeonlan/](http://gsd.di.uminho.pt/jpo/software/wakeonlan/)

they have a little howto here:
[http://gsd.di.uminho.pt/jpo/software/wakeonlan/mini-howto/](http://gsd.di.uminho.pt/jpo/software/wakeonlan/mini-howto/)

Hope you get it sorted.  I'll be getting a squeezebox soon and I would also like this feature to work.

Let us know how it works out.   :)

---

