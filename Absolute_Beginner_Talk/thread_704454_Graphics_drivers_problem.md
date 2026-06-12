---
title: "Graphics drivers problem"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by boblettoj99 on 2008-02-22
Ok i have a big problem with my graphics, iv'e been trying all day to get the drivers installed but to no luck. I have an ATI radeon xpress 200 which came with my Dell inspiron 1501. Here is the stuff from hwinfo:

```

31: PCI 105.0: 0300 VGA compatible controller (VGA)
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1002_5975
  Unique ID: ul7N.b8fSahFKZR1
  Parent ID: vSkL.dQFUNbiC_g9
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:05.0
  SysFS BusID: 0000:01:05.0
  Hardware Class: graphics card
  Model: "Dell Radeon XPRESS 200M 5975 (PCIE)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x5975 "Radeon XPRESS 200M 5975 (PCIE)"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x01f5
  Memory Range: 0xc8000000-0xcfffffff (rw,prefetchable)
  I/O Ports: 0x9000-0x9fff (rw)
  Memory Range: 0xc0100000-0xc010ffff (rw,non-prefetchable)
  Memory Range: 0xc0120000-0xc013ffff (ro,prefetchable,disabled)
  IRQ: 10 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d00005975sv00001028sd000001F5bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: radeon
  Driver Info #1:
    XFree86 v4 Server Module: fglrx
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #12 (PCI bridge)

```

I tried going to the ATI website and downloaded this file:
ati-driver-installer-8-02-x86.x86_64.run

i installed that and it put the ATI catalyst control centre thing in my menu but when i click on it it brings up an error (screenshot):

[http://i41.photobucket.com/albums/e254/frahasio/snapshot1.png](http://i41.photobucket.com/albums/e254/frahasio/snapshot1.png)

possibly cos i downloaded the wrong thing? i dont know!
im new to linux so be nice :)

version = kubuntu 7.10

---

### Post by Therion on 2008-02-22
Try using [Envy](http://albertomilone.com/nvidia_scripts1.html). 

It will download and install the correct restricted driver for your PC,  and then configure the x-org.conf file for you automatically.
The error MIGHT be caused by the fact that you are installing ATI's restricted driver, but I don't know for sure.

---

### Post by boblettoj99 on 2008-02-22
I already tried envy, when i ran it, it brought up this message:

some dependencies are missing, envy will not work without them..
i still have it installed so if you know how to get round that, i could do it with envy

---

### Post by boblettoj99 on 2008-02-22
bump :(

---

### Post by boblettoj99 on 2008-02-22
hmmm catalyst control center has suddenly started working :s

however when i play counter strike: source (the main reason for the whole graphics drivers thing) it still has a very low fps.
i am running it through crossover linux, can anyone help?

---

