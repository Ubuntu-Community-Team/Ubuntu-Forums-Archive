---
title: "Ubuntu 10 no me deixa utilitzar l'escaner."
date: 2011-01-15
forum: Catalan Team
---

### Post by sanau3 on 2011-01-15
Tinc un scaner scanworks 600U i no puc escanetjar. El sistema el detecta aquí teniu la copia del lsusb -vv:

Bus 003 Device 002: ID 0461:0364 Primax Electronics, Ltd LG Electronics Scanworks 600U Scanner
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0461 Primax Electronics, Ltd
  idProduct          0x0364 LG Electronics Scanworks 600U Scanner
  bcdDevice            0.02
  iManufacturer           2 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x40
      (Missing must-be-set bit!)
      Self Powered
    MaxPower               48mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        16 
      bInterfaceSubClass      1 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
cannot read device status, Operation not permitted (1)
Som nou a l'ubuntu, necesito ajuda.

---

### Post by wgarcia on 2011-01-15
Hi ha una pàgina del projecte "sane" que és el que s'encarrega de fer funcionar els escàners per a linux, i lamentablement em sembla entendre de la pàgina que el teu model no està suportat. 

A l'enllaç 

[http://www.sane-project.org/sane-mfgs.html#Z-PRIMAX](http://www.sane-project.org/sane-mfgs.html#Z-PRIMAX)

hi ha la informació dels models d'escàner de Primax, que sembla ser el fabricant del teu model. No he trobat cap model que es digui "scanworks" però sí que hi ha un que es diu "Colorado 600u" i diu clarament que no està suportat. 

El problema deu ser que aquest fabricant sols proveeix controladors de codi tancat i propietaris, i no per a Linux sinó per a d'altres sistemes operatius, i com no dóna informació tampoc els desenvolupadors de linux poden fer res. Així és com es perpetua el monopoli que tots coneixem.

---

