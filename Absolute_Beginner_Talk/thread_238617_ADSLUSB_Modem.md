---
title: "ADSL/USB Modem"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by peadenm on 2006-08-17
ok, here's the deal...i'm completely new to linux. i now have a dual boot system (ubuntu/win xp pro). everything has gone smoothly with the exception of my browsing capabilities. i live in italy, and i use an italian service provider (telecom italia). along with that comes the italian adsl modem ("web power adsl"). everything that i have read about modems has been for ethernet. i have an rj11 connection to the adsl modem and then it's a usb connection to my computer. i have the installation cd for the modem but don't quite know how to use it in ubuntu. i dont know that you can use the modem without running the setup.exe from the disk. not sure though. if anyone could help me get across this hurdle, i would greatly appreciate it.

---

### Post by dmizer on 2006-08-18
usb is an absolutely terrible interface for dsl (true in windows and linux).  your best, easiest, most headache free solution here is to bug telecom italia into supplying you with a real modem with an ethernet interface.

that asside, we will need to know more about your usb modem than just it's name.  we will need to know it's chipset as well as what linux calls the device.

you can find at least some of the information you will need by connecting your modem and posting the output of:
```
lspci | grep USB && dmesg | grep USB
```

---

### Post by peadenm on 2006-08-18
ok, i'll check it out when i get off work. thanks.

---

