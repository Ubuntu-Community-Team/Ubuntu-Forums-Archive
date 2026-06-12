---
title: "stuck when 94%[installation]"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by 3076 on 2008-02-19
when installing base system come to install extra packet(94%),it get stuck!this is the picture[ATTACH]60182[/ATTACH]:
when i press alt+F4,it appears this:
[ATTACH]60183[/ATTACH]
the last three lines says(please look up the picture for exact detail):
...sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVE_SENSE,SUGGEST_OK
...sr 1:0:0:0: [sr0] Sense Key :Medium Error[current]
...sr 1:0:0:0: [sr0] Add.Sense:CIPC unrecovered error
...end_request: I/O error, dev sr0,sector 324

can you explain it for me?
thanks

---

### Post by szymon_g on 2008-02-19
did you checked MD5Sum of cd image before and after writinig it to disc?

---

### Post by kristjans on 2008-02-19
Agreed with the last poster, check your CD for defects before trying to install. Either that, or your hard disk/partition got full.

---

