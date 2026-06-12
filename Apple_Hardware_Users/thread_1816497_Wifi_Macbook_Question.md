---
title: "Wifi Macbook Question"
date: 2011-08-02
forum: Apple Hardware Users
---

### Post by Jac0bSummerz on 2011-08-02
Hi! I got Ubuntu 11.04 64 bit installed on a 2011 Macbook Pro with a core i5. I'm dual booting with os x. The Wifi on os x works but when I use Ubuntu it doesn't detect any networks. Any Ideas?

---

### Post by blane2 on 2011-08-02
[https://help.ubuntu.com/community/MacBookPro8-1/Natty](https://help.ubuntu.com/community/MacBookPro8-1/Natty)

> As of this writing, very little of the extended hardware in the MBP appears to function correctly in Ubuntu.

---

### Post by Jac0bSummerz on 2011-08-02
When I type sudo dmidecode -s system-product-name in terminal it says MacbookPro8,1

---

### Post by blane2 on 2011-08-02
> **Jac0bSummerz said:**
> When I type sudo dmidecode -s system-product-name in terminal it says MacbookPro8,1

see link above for compatibility, issues and work-arounds for your model.

broadcom is working on linux compatibility drivers for your wireless card right now, but it's not available as of yet.

---

