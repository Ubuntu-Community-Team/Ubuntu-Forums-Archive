---
title: "Wifi works but can no longer detect SSID"
date: 2017-07-11
forum: Apple Hardware Users
---

### Post by astralliam on 2017-07-11
Hi, using Ubuntu 16.04 on my Macbook Pro 2012. 

I wifi GUI is no longer able to detect SSIDs. If I manual add an SSID to the list in 'Edit Connections...' I can use WiFi no problem. 

BCM4331

---

### Post by ajgreeny on 2017-07-11
*Thread moved to **Apple Hardware Users**.* which is more appropriate and a better fit.

---

### Post by efflandt on 2017-07-11
Is it unable to detect any SSID's or just not yours? Does your wireless router or AP have SSID broadcast disabled?


Do you see details on your or any more SSID's from your neighbors than the gui, if in a terminal you do:```
sudo iwlist scan
```

---

### Post by astralliam on 2017-07-13
SSID are shown when I run 'iwlist scan' but no SSIDs ever show up in the GUI version.

---

