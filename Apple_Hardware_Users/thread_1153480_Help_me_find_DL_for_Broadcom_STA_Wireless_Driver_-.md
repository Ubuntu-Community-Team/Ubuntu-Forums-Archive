---
title: "Help me find DL for Broadcom STA Wireless Driver - Macbook 4,1"
date: 2009-05-08
forum: Apple Hardware Users
---

### Post by transmition on 2009-05-08
I want to upgrade my kernel in order to help fix some of the problems with my intel graphics. However, by doing so I deactivate my wireless driver for my macbook 4,1. Can someone point me to a download link for the Broadcom STA Wireless Driver that comes with a fresh install and is listed under System->Administration->Hardware Drivers?

Any help would be greatly appreciated.

---

### Post by transmition on 2009-05-08
---

---

### Post by pxwpxw on 2009-05-08
> **transmition said:**
> I want to upgrade my kernel in order to help fix some of the problems with my intel graphics. However, by doing so I deactivate my wireless driver for my macbook 4,1. Can someone point me to a download link for the Broadcom STA Wireless Driver that comes with a fresh install and is listed under System->Administration->Hardware Drivers?

Any help would be greatly appreciated.

This is what I used, after google broadcom STA, fpr bcm4328 on mbp4,1 (not mb4,1).

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
The README.txt is a good start.

---

### Post by transmition on 2009-05-08
Will this work with my macbook? I don't think the MBP uses the same driver as the macbook 4,1.

---

### Post by pxwpxw on 2009-05-09
> **transmition said:**
> Will this work with my macbook? I don't think the MBP uses the same driver as the macbook 4,1.
What does lspci say -
```

pxw@mbp:~$ lspci -nn | grep Net
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 05)
pxw@mbp:~$ 

```

---

### Post by transmition on 2009-05-09
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
```

---

### Post by pxwpxw on 2009-05-09
> **transmition said:**
> ```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)
```

Looks close enough.

---

