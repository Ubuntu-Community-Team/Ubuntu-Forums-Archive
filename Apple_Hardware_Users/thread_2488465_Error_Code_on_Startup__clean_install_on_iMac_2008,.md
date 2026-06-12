---
title: "Error Code on Startup / clean install on iMac 2008, Ubuntu 23.04"
date: 2023-07-05
forum: Apple Hardware Users
---

### Post by enahssmith on 2023-07-05
For the most part I'm amazed everything actually works on a computer that is 15 years old. The only problem I'm getting is an error code on startup. Whatever it is it's causing it too load slow but once it does everything seems to work.
The code is: Bluetooth: hci0: unexpected event for opcode 0x0000.
Any ideas?]

---

### Post by Rubi1200 on 2023-07-05
Do you have Bluetooth enabled on the system? Any devices connected?

---

### Post by MAFoElffen on 2023-07-05
Please post the output of this within CODE Tags:
```

grep 'AutoEnable=' /etc/bluetooth/main.conf

```

---

### Post by QIII on 2023-07-05
Moved to **Apple Hardware Users**.

---

