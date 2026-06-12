---
title: "boss linux issue"
date: 2012-06-12
forum: Any Other OS
---

### Post by hkreddy4u on 2012-06-12
i have installed boss Linux , and also configured it as windows active directory member using **Power Broker® Identity Services Open Edition .**  i can able to ping my windows DC and gate way but i am getting error 502 bad gateway and INTERNET is not working .kindly help me to resolve this issues....   thank you....

---

### Post by sanderj on 2012-06-12
Internet not working, but you can ping other computers on the LAN?

What's the output of

```
mtr -nrc2 8.8.8.8

```


And: are you on a company LAN, or a private LAN?

---

### Post by lisati on 2012-06-12
*Thread moved to **Other OS/Distro Talk**.*

---

