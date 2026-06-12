---
title: "Dapper on Armada 7800 No Sound ES1688 ISA soundcard not detected"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by gigi1234 on 2006-10-01
I just installed Dapper on an old Compaq Armada 7800. Everything is great except there is no sound. Modprobe fails to detect the soundcard, which I have gathered is an ES1688 ISA type card. I understand that support for this type of card is poor in Ubuntu. Can anyone get me started on a solution? I have read several guides and howtos but the advice either doesn't work or seems over my head.

Thanks!

---

### Post by gigi1234 on 2006-10-01
I added "snd-es1688" to /etc/modules and rebooted-then the sound seemed to work. But upon login the drumbeat sound goes crazy and keeps repeating and repeating.

---

