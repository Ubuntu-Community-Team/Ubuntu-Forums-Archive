---
title: "Problems instaling Ubuntu"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by CrazY^ on 2007-09-15
hi there .. i have some problems instaling ubuntu from boot disk , when i try to instal it , has this error and i waiting 15 minutes and nothing happens ...

-MP-BIOS Bug : 8254 timer not connected to I0-APIC
-Kernel panic - not syncing:I0-APIC +timer doesn't work ! Boot with apic=debuger and send a report , then try booting withthe 'noapic' option

plz tell me what to do ..

---

### Post by Steve1961 on 2007-09-15
You could try adding 

noapic nolapic

to the boot options

Note: from what I remember I think you have to pres F6 at the initial splash screen for 'other options'. You can then add these options to the end of the command line

---

### Post by CrazY^ on 2007-09-15
thanks that works :)

---

