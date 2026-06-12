---
title: "nvidia unknown"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by GQed76 on 2007-02-13
when i type lspci my nvidia card is shown as 

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 02e1 (rev a2)


Is this normal.  Ive compiled ther kernel myself.

---

### Post by mikewhatever on 2007-02-13
It is not normal, but the reason might be, that either there is not driver for it, or the driver is not loaded. Have you got the driver installed?

---

### Post by tronica on 2007-02-13
it seems that newer cards are that way, however thats just my experience, what card do you have and do you have the drivers installed?

---

### Post by GQed76 on 2007-02-15
a 7600 and yes the drivers are installed and working

---

### Post by tronica on 2007-02-15
but the card is working fine with the drivers, so i wouldn't worry about it, I can't say whether or not its normal, it just seems that ubuntu didn't recognize the card's name. I have a ATI x1800GTO, its the same way.

---

### Post by hrp2171 on 2007-02-15
Yes, that's normal.  As long as the driver works and lspci shows nVidia Corp. it's all good.

It startled me at first, too.  :)

---

### Post by paddyS on 2007-02-15
I have the same card (GF go 7600) it didn't work until the nvidia driver was installed but the nvidia website claims this is not supported by the driver - I guess it will get updated at some point. 

Mine still claims it's unknown but it knows its an nvidia card and as it's working I guess thats enough!

---

