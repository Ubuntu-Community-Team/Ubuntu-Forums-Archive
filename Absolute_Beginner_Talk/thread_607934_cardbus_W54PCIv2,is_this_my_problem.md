---
title: "cardbus W54PCIv2,is this my problem"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by petsno123 on 2007-11-09
Using the above PCI card in WindowsXP is OK.Trying to connect up in ubuntu7.04 is not so.SSID is recognised and the WEP password but that's all.Card has a linux driver,so I assumed things would be OK.What can  I doto solve this problem,please.

---

### Post by anewguy on 2007-11-09
From a little research, it appears you may be needing the raillink(? drivers - like rt2500.  First we need to know the chipset, so please do the following and post the results back here.  I will be gone for about 1 1/2 hours or so (I'm in the US and have a couple of errands I must do).

In a terminal window (if you don't know this, click "Applications" then scroll down to "Accessories" then over and down to "Terminal" and click):

lspci    <enter>

Do this with your wireless card plugged in.  Hopefully it will show - if not just post back that it didn't show up.

I'll be back in a little bit and check things out.:)

---

### Post by anewguy on 2007-11-10
Please post back if you need help with this.  I think you will need to use the above mentioned drivers and perhaps ndiswrapper.

---

