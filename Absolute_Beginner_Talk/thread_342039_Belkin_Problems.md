---
title: "Belkin Problems"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by melenor on 2007-01-19
i am a complete newbie to Ubuntu having just recently installed it, after hearing so much about Linux, but the biggest problem i have is that i can't access the internet, the problem is the Belkin Wireless G USB Network Adapter. it works fine in windows but doesn't work in Ubuntu and also my belkin mouse side buttons don't work ubuntu, i need the real basic, i barely know anything of ubuntu.
 my mouse does work but not the back/forward buttons.
Thanks for helping me

---

### Post by melenor on 2007-01-19
i have looked online a little bit more and found something about chipsets for the wireless adaptor but i still don't understand how to find out what chipset it has

---

### Post by melenor on 2007-01-20
can somebody please help me out i know three posts in a row is bad but my thread keeps getting pushed down every five minutes

---

### Post by JamieC on 2007-01-20
Hey, please open a new terminal (Applications -> Accessories -> Terminal) and post the output of the following command:-

For USB Device:
```

lsusb | grep Belkin

```

For PCI Device:
```

lspci | grep Belkin

```

---

### Post by melenor on 2007-01-20
it didn't give me any information and the adaptor is USB and pluged in 
i don;t know how to upload a picture but i took a screen shot of what it said

---

### Post by JamieC on 2007-01-21
Okay, can you just post the output of the following commands please:
```

lspci
lsusb

```

---

