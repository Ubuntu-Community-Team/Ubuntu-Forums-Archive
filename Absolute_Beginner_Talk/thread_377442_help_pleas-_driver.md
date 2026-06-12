---
title: "help pleas- driver"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by nati1966 on 2007-03-06
i install ubuntu 6.10 from dvd 
and i have problem in the ethernet.
where can i download driver.
i have a ""foxconn P9657AA mainboard""

pleas help

---

### Post by 3rdalbum on 2007-03-06
What is your ethernet problem exactly? Can you ping any of the other computers on your network?

```
ping 192.168.1.100
```

(or whatever the IP address is of the other computer)

---

### Post by nati1966 on 2007-03-06
its on board lan
and ubunto didnt racnizd it (no lan)
sorry for my english.

thnks.

---

### Post by chili555 on 2007-03-06
We need to know what kind of ethernet chipset you have in order to help. Open a terminal and type: ```
lspci -v | grep Ethernet
``` You will see detailed identification of your ethernet chipset.

If it is Marvell, hop over to the Networking and Wireless forum: [http://www.ubuntuforums.org/forumdisplay.php?f=136](http://www.ubuntuforums.org/forumdisplay.php?f=136) and search for "Marvell"

---

### Post by nati1966 on 2007-03-06
it is marvell yukon nic

pleas help
i dont knoh linx at all

can samone tell me what to do step by step what to download and how to install.
thnks.

---

