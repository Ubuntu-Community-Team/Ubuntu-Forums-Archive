---
title: "disabling direct memory access (dma) in ubuntu"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by cf1709 on 2007-04-22
when i was using windows, enabling dma in the secondary ide keeps my dvd drive (sony dvdrw dru820a) from reading/writing properly but disabling the dma fixes it. i noticed that the same thing is happening in ubuntu. is there any way i can disable dma in ubuntu (6.10 user)? thanks!:)

---

### Post by Bachstelze on 2007-04-22
```
sudo hdparm -d0 /dev/whatever
```

---

