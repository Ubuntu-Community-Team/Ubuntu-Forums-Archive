---
title: "Wifi Seems to not be running"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by agnosticspacemonkey on 2006-04-04
I just installed Ubuntu on my laptop.  It is an Acer Aspire 3003LCi,and contains a Mobile AMD Sempron Processor 3000+.  Installation was successfull, except for my wireless network. Ubuntu seems to not recognize my Card ( which is  a Wifi 802.11b/g wireless Lan). I am now getting internet through a cable, but it still cannot configure the system.  If anyone has the cure, please let me know.


EASM

---

### Post by johnnymac on 2006-04-04
It could be that your card requires specific software to work (ndiswrapper or madwifi).  Do this from a terminal:

```

lspci |more

```

Look for a part that talks about 802.blahblah....

Copy that and post it back here.  There are different how-to's depending on the driver type of the wifi card you use.

---

