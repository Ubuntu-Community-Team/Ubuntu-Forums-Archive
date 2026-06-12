---
title: "MAKEDEV, MKNOD and modems"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-01-12
I have a modem (internal, controller or hardware based) that Dapper will only call /dev/ttyS4. GnomePPP can't find it or some other "internal" problem. The modem (well, wvdial and pppd) hold the line for a time, then drop it. Actually sometimes the telephone line hangs-up and othertimes, the modem is still online, but there is no connection to the net.

I need help with making Dapper "think" there is a /dev/modem that is a real link or workaround to /dev/ttyS4.

Thanks.

---

### Post by Bachstelze on 2007-01-12
Have you tried just making a symlink ?

```
sudo ln -s /dev/ttyS4 /dev/modem
```

---

### Post by Mark_in_Hollywood on 2007-01-13
Yes, and I can't confirm that it matters that I did the 

ls -s /dev/ttyS4 /dev/modem

the modem's wvdial and pppd and ancillary files still are fighting each other.

---

