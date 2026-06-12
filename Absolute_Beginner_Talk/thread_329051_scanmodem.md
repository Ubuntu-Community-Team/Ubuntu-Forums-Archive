---
title: "scanmodem"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by oilchangeguy on 2006-12-31
just downloaded scanmodem from the linmodem.org site, but the commands to run it make no sense. does anybody know the correct command order to make this run. using a toshiba laptop, so no way to pull the card and read the chipset. don't need the modem for internet access, use highspeed. but would like to be able to send and recieve faxes. thanks.

---

### Post by seijuro on 2006-12-31
odds are you should be able to find out just by running lspci here is what mine looks like.
```

0000:00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)

```

The driver support for winmodems in linux is pretty poor. Unfortunately my chipset requires drivers from the <insert bad language here> linuxant people. Who "sell licenses" to enable full use of their closed drivers. I'm sure I'm not the only person who feels this is completely against the linux mindset and should be discouraged.

---

### Post by oilchangeguy on 2006-12-31
thanks for the tip. modem not listed. this is an older toshiba laptop (satellite 1805-s177) that i use to experiment with. running a celeron 800mhz cpu, 512mb ram, and a small collection of harddrives that i switch when needed. they are a 20gb hd w/a factory fresh install (via the restore disk) of win ME, a 40gb hd w/a fresh install of win xp pro, and a 40 gb hd w/a fresh install of ubuntu 6.06. so i guess i'll just have to switch to the xp hd if i actually need access to the modem.

---

