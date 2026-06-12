---
title: "how to display video card pci bus ID number"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by elchico04 on 2008-03-15
I dont remember how I did it but I remember that I typed something into the terminal and it spit out my video devices and their BUS ID #s.

It wasn't lspci, that gives me the bus IDs in a format that I don't understand.


Anyone know how I can do this?

---

### Post by dcstar on 2008-03-15
> **elchico04 said:**
> I dont remember how I did it but I remember that I typed something into the terminal and it spit out my video devices and their BUS ID #s.

It wasn't lspci, that gives me the bus IDs in a format that I don't understand.


Anyone know how I can do this?

lswh?

---

### Post by elchico04 on 2008-03-15
i get "command not found" when I type that

---

### Post by wesley_of_course on 2008-03-15
> **elchico04 said:**
> i get "command not found" when I type that

    How about lsusb ?   I'd thought lspci woulda worked  , shows what I know !
  Hope it helps.

---

### Post by Shazaam on 2008-03-15
You guys were close. :)
```
sudo lshw
```
Shows pretty much everything.

---

### Post by dcstar on 2008-03-15
> **Shazaam said:**
> You guys were close. :)
```
sudo lshw
```
Shows pretty much everything.

Sorry, dyslexic typign.......      :)

---

### Post by wesley_of_course on 2008-03-15
> **Shazaam said:**
> You guys were close. :)
```
sudo lshw
```Shows pretty much everything.

   Thanks Shazaam !  list , show , hardware ?

>  wesley@Ratdog:~$ sudo apt-get install hwinfo
[sudo] password for wesley:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libhd13
The following NEW packages will be installed:
  hwinfo libhd13
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 633kB of archives.
After unpacking 1753kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe libhd13 13.35-1 [589kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe hwinfo 13.35-1 [43.9kB]
Fetched 633kB in 4s (134kB/s)
Selecting previously deselected package libhd13.
(Reading database ... 196142 files and directories currently installed.)
Unpacking libhd13 (from .../libhd13_13.35-1_amd64.deb) ...
Selecting previously deselected package hwinfo.
Unpacking hwinfo (from .../hwinfo_13.35-1_amd64.deb) ...
Setting up libhd13 (13.35-1) ...

Setting up hwinfo (13.35-1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

wesley@Ratdog:~$ hwinfo --gfxcard
43: PCI 100.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_10de_391
  Unique ID: VCu0.7yMrh_0yuq9
  Parent ID: 3hqH.Dl4y9PyOsZE
  SysFS ID: /devices/pci0000:00/0000:00:03.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "eVga.com GeForce 7600 GT"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0391 "GeForce 7600 GT"
  SubVendor: pci 0x3842 "eVga.com. Corp."
  SubDevice: pci 0xc615 
  Revision: 0xa1
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xfa000000-0xfaffffff (rw,non-prefetchable)
  Memory Range: 0xe0000000-0xefffffff (rw,prefetchable)
  Memory Range: 0xfb000000-0xfbffffff (rw,non-prefetchable)
  I/O Ports: 0xcf00-0xcf7f (rw)
  Memory Range: 0xfcfe0000-0xfcffffff (ro,prefetchable,disabled)
  IRQ: 16 (4769831 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd00000391sv00003842sd0000C615bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: nv
  Driver Info #1:
    XFree86 v4 Server Module: nvidia
    3D Support: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #28 (PCI bridge)

Primary display adapter: #43

---

