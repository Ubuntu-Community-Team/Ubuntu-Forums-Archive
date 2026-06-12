---
title: "How to connect to internet? Help!"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by caspar88 on 2006-11-11
Just installed version 6.06 but seems there is no Dial up networking to configure internet settings?
Where can I find instructions to help me to do this?
Thanks.

---

### Post by Teamgeist on 2006-11-11
I never did this myself since I'm sitting behind a router that connects me to the internet, but try this and follow the instructions given on the screen:

```
sudo pppoeconf
```

---

### Post by caspar88 on 2006-11-11
Hi
Tried sudo pppoeconf command and I get:

1 device found eth0
It scans the device and reports that Access concentration did not respond?
Anyone know what this means?
(The ADSL light on my broadband modem is not showing)
Thanks

---

### Post by navneeth on 2006-11-11
Make sure there are no loose wires. Check the instructions here
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html)
(it's good to bookmark help.ubuntu.com, btw). If it's any other type, just scroll to the appropriate connection.

---

### Post by gargoyle on 2006-11-11
What are you trying to use as your modem?
If it is an internal modem chances are it is Window soft modem.
If so you need to go to the [DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto")

There is a program Scanmodem that will help you.

Win modems are tough to set up in any form of Linux.

---

