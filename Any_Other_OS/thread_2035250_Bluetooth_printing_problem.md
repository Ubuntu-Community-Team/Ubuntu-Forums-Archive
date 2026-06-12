---
title: "Bluetooth printing problem"
date: 2012-07-30
forum: Any Other OS
---

### Post by coldraven on 2012-07-30
Hi all, I'm trying to print via Blutooth to my Epson Stylus Photo R300.
I  have tried with two different cheap dongles but not the expensive Epson  BT dongle. The dongle plugs into the printer, my laptop has BT built-in
I can send an image to the printer from my laptop (only JPG or TIFF) but cannot print from an application, Gimp for example. It tries but just stalls and says that the printer is idle.
 I think what is missing is the  Hardcopy Cable Replacement Profile, but to be honest I really don't know.
I originally posted this on the Mint forums but did not get any answers, hopefully someone here can help.
Can anyone tell me from the following output if this is possible, thanks
```
~ $ sudo hcitool info 00:15:83:3D:0A:57
[sudo] password for coldraven: 
Requesting information ...
   BD Address:  00:15:83:3D:0A:57
   Device Name: Stylus Photo R300-0
   LMP Version: 2.0 (0x3) LMP Subversion: 0xc5c
   Manufacturer: Cambridge Silicon Radio (10)
   Features: 0xff 0xff 0x8f 0xfe 0x9b 0xf9 0x00 0x80
      <3-slot packets> <5-slot packets> <encryption> <slot offset> 
      <timing accuracy> <role switch> <hold mode> <sniff mode> 
      <park state> <RSSI> <channel quality> <SCO link> <HV2 packets> 
      <HV3 packets> <u-law log> <A-law log> <CVSD> <paging scheme> 
      <power control> <transparent SCO> <broadcast encrypt> 
      <EDR ACL 2 Mbps> <EDR ACL 3 Mbps> <enhanced iscan> 
      <interlaced iscan> <interlaced pscan> <inquiry with RSSI> 
      <extended SCO> <EV4 packets> <EV5 packets> <AFH cap. slave> 
      <AFH class. slave> <3-slot EDR ACL> <5-slot EDR ACL> 
      <AFH cap. master> <AFH class. master> <EDR eSCO 2 Mbps> 
      <EDR eSCO 3 Mbps> <3-slot EDR eSCO> <extended features> 

```

---

### Post by Perfect Storm on 2012-07-30
Moved to Other OS/Distro Talk.

---

