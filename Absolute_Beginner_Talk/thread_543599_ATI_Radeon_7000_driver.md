---
title: "ATI Radeon 7000 driver"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by petit.padavoine on 2007-09-05
3D Acceleration is working with my ATI Radeon 7000 card and the open-source driver.

However, Compiz Fusion is pretty slow, and someone recommended using fglrx and xgl, instead of the open-source drivers and aiglx.

I downloaded fglrx, replaced "ati" with "fglrx" in my xorg.conf, rebooted... No X. Error message: no screens detected.

I've also heard mentioned that actually the Radeon 7000 is NOT supported by fglrx :confused:.

So does fglrx actually support a Radeon 7000, will using fglrx and xgl speed up my Compiz, and how can I fix the no screens detected error?

---

### Post by overdrank on 2007-09-05
> **petit.padavoine said:**
> 3D Acceleration is working with my ATI Radeon 7000 card and the open-source driver.

However, Compiz Fusion is pretty slow, and someone recommended using fglrx and xgl, instead of the open-source drivers and aiglx.

I downloaded fglrx, replaced "ati" with "fglrx" in my xorg.conf, rebooted... No X. Error message: no screens detected.

I've also heard mentioned that actually the Radeon 7000 is NOT supported by fglrx :confused:.

So does fglrx actually support a Radeon 7000, will using fglrx and xgl speed up my Compiz, and how can I fix the no screens detected error?

HI this is a link to the "how to" I used to install on a ATI 7500
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
Hope this helps and good luck!

---

### Post by petit.padavoine on 2007-09-05
Your guide uses open-source drivers and aiglx. I'm trying to get fglrx, the closed-source proprietary ATI driver, to work.

---

### Post by zit on 2007-09-05
- Me too same problem with this card
 and i have got white screen :

[http://img159.imageshack.us/img159/9385/compizzz4.jpg](http://img159.imageshack.us/img159/9385/compizzz4.jpg)

i use free driver radeon.

- Moi aussi même probleme avec cette carte graphique
et j'ai écran blanc :

[http://img159.imageshack.us/img159/9385/compizzz4.jpg](http://img159.imageshack.us/img159/9385/compizzz4.jpg)

J'utilise le driver libre radeon.

---

### Post by Hobo Joe on 2007-09-05
Use Envy. I have a link in my sig.

---

### Post by zit on 2007-09-05
```
ENVY ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk.
```

error

---

### Post by Npl on 2007-09-05
fglrx driver only supports Cards based on R200 and above (Radeon 8500 and up).  With a Radeon 7000  the OS-Driver is your only option.

---

### Post by zxscooby on 2007-12-18
i have had fglrx working with this card before ,it worked great but i cant get it to work with gutsy.

---

