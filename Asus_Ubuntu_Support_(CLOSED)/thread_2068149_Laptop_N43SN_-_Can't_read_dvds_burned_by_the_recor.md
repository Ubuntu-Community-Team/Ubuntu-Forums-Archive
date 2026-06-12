---
title: "Laptop N43SN - Can't read dvds burned by the recorder"
date: 2012-10-08
forum: Asus Ubuntu Support (CLOSED)
---

### Post by italomaia on 2012-10-08
Hi. I'm having a problem where my laptop dvd drive does not recognizes data dvds burned by itself. I'm having to use a external dvd drive to read my dvds. This is absolutely weird because my laptop drive records just fine. Using xubuntu 12.04. Ubuntu had the same problem.

**dmesg | grep "sr0"**
[12331.669921] sr 2:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12331.669929] sr 2:0:0:0: [sr0]  Sense Key : Medium Error [current] 
[12331.669939] sr 2:0:0:0: [sr0]  Add. Sense: Cannot read medium - unknown format
[12331.669951] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[12331.669972] end_request: I/O error, dev sr0, sector 0

---

### Post by albandy on 2012-10-08
Try recording it at lower speed.

---

