---
title: "right time zone ,wrong time"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-01-29
when i installed edgy 6.10 i set the time zone to australia/perth,
which is correct but the time is nearly twelve hours out,i have adjusted the time ,
but every time i shut down and reboot it reverts to the old time.

so is this a fixable problem or just have to put up with it

thanks:D

---

### Post by b_martinez on 2007-01-29
> **STREETURCHINE said:**
> when i installed edgy 6.10 i set the time zone to australia/perth,
which is correct but the time is nearly twelve hours out,i have adjusted the time ,
but every time i shut down and reboot it reverts to the old time.

so is this a fixable problem or just have to put up with it

thanks:D

It's fixable. Do you have your computer set up to keep the time updated with 'ntp'? The network time protocol daemon will keep your system updated using a 'pool'  time server, or you can find a local one. Look in the repositories for ntp, and install it if you haven't got it yet.
hth
Bill

---

### Post by STREETURCHINE on 2007-01-29
thanks that seemed to work,it even corrected the god forsaken daylight savings time that the gov enforced on us,

 thank you:D

---

