---
title: "HP LaserJet papersize stuck at A4"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Iowan on 2006-10-26
Although **/etc/papersize** is stuck at A4 in Dapper as well as Edgy, my Dapper setup will print a test page to my HP LaserJet 5M networked (JetDirect) printer.  Edgy (despite the same settings) results in:
**TRAY 2 LOAD A4**
It doesn't seem to matter which tray or paper size I select.
(I DID change **/etc/papersize** to **letter**, but results remain the same.

---

### Post by mitch.c on 2006-10-27
> **Iowan said:**
> Although **/etc/papersize** is stuck at A4 in Dapper as well as Edgy, my Dapper setup will print a test page to my HP LaserJet 5M networked (JetDirect) printer.  Edgy (despite the same settings) results in:
**TRAY 2 LOAD A4**
It doesn't seem to matter which tray or paper size I select.
(I DID change **/etc/papersize** to **letter**, but results remain the same.
Change /etc/papersize to letter and re-install the printer.

---

### Post by Iowan on 2006-10-30
That worked... but dunno why Dapper works w/ **papersize=A4**:confused:

---

