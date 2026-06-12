---
title: "USB stick problem"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by peakshysteria on 2008-03-08
My daughters newest machine running Gutsy fail to detect USB sticks in the front slots. External drives work just fine. But USB stick aren't recognized. The strange thing is that the slots in the back of the machine works just nice. But it's a drag to pull the machine form underneath the desk every time we're in need of a USB stick. And off course it the principal of it. It should work in all slots. :(

Any takers?

---

### Post by JoshuaRL on 2008-03-08
Could you try:
```

lsusb

```

---

### Post by mdebusk on 2008-03-08
> **peakshysteria said:**
> My daughters newest machine running Gutsy fail to detect USB sticks in the front slots. External drives work just fine. But USB stick aren't recognized.

Are you trying some off-brand USB sticks? I have one no-name that I can't get *any* computer to recognize.

Does the computer's manual say anything about the differences between the front and back slots?

---

### Post by stoneybroke on 2008-03-08
Are you sure that the front USB ports are connected to the motherboard? I have known new computers "shop built" not to have connected the front USB ports before.

---

### Post by peakshysteria on 2008-03-09
> **JoshuaRL said:**
> Could you try:
```

lsusb

```

The output from lsusb:

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 045e:00e1 Microsoft Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Have tried different USB sticks. So it's not the brand or the stick itself. Other machines handle them well. My own Gutsy recognize the sticks as well. The machine is a private build (not by myself). But as i said; external drives work nicely from the slots in the front.

---

### Post by EdThaSlayer on 2008-03-09
Maybe the guys who created this computer never connected the two slots in the front. It's a common issue, if you can't get any other USB devices it's because no power/connection is being provided to those front slots. It was like that with one of my computers.

---

### Post by JoshuaRL on 2008-03-09
Thanks for that peakshysteria.  Could you try:
```

lsusb -v -s [[004]:][002]]

```

I'm not that sure if the command is correct, I looked it up on Google.  I'm asking it to be verbose about that bus id and device id.

---

