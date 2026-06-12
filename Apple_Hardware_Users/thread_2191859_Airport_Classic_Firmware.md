---
title: "Airport Classic Firmware"
date: 2013-12-04
forum: Apple Hardware Users
---

### Post by rsavage on 2013-12-04
I've posted these before on another forum, but that seems to be down at the moment.....

If you have an airport classic card and are having problems (v likely due to an incorrect ap_scan value), then can you try out the attached alternative firmware please?

Background info: [https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F](https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F)

Can you use WEP with any version of firmware beyond 8.70?

Do the 9.42 or 9.52 versions of firmware pass the correct ap_scan value to network manager?  To check:
```

*grep ap_scan* [I]/var/log/syslog
[/I]
```[I]


Thanks!

[/I]sha256sum agere_fw_9.42.zip
e63fc4228f52f8fb0d4dd923999448f98e9284b1b5b69b615281a6a10c5b76e2  agere_fw_9.42.zip

sha256sum agere_fw_9.52_9.40.zip
8c5066fc257cdaf51baeb0a80bd71554b3531dd8a5699a99cc1b5a442adb9967  agere_fw_9.52_9.40.zip

---

### Post by dand1972 on 2013-12-06
For me, ```
grep ap_scan /var/log/syslog
``` returns ```
set interface ap_scan to 1
```  This is with the original firmware, and 9.42 and 9.52 as well.  I can connect to WPA with all versions.

I was having trouble connecting with the original firmware in the beginning, but I think that was because I hadn't switched my router to TKIP yet.  When I switched it, I connected successfully with 9.42 and 9.52, and when I reverted to the original firmware it worked, too.

---

### Post by rsavage on 2013-12-08
Thanks Dan!

For completeness, do you know if the 8.70 firmware (I guess that will be the version you have flashed on your card) also gives ap_scan=1?

It is interesting that you haven't had problems with your card.  I think it very much depends on your wifi network setup and the amount of other networks in the area.

I'll update the FAQ based on your findings.

---

### Post by dand1972 on 2013-12-09
8.70 gives the same ap_scan=1.  I think mine works because I click my heels three times before connecting.

---

