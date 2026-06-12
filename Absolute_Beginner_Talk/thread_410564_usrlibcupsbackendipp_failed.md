---
title: "/usr/lib/cups/backend/ipp failed"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by stevieb on 2007-04-15
i'm trying to set up remote printing between my laptop (edgy) and server (dapper).  when i send a test page from the cups web browser interface, i get the following error:

```
/usr/lib/cups/backend/ipp failed
```

my printer is at ipp://<myhost>/ipp/parport0

thanks for any help; let me know if i need to post more info

-steve

---

### Post by stevieb on 2007-04-16
fixed it; my correct printer uri is
```

ipp://<ipaddress>/printers/HP_LaserJet_6L
```

Thanks to those who looked!

-steve

---

