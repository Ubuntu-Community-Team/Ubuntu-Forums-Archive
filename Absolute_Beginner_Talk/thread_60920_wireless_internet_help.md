---
title: "wireless internet help"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by CoFFeY on 2005-08-29
ok im am noob with linux, i need to setup my wireless internet linksys wmp54g i don't know how to use ndiswrapper can someone help?

---

### Post by atoponce on 2005-08-29
First you need to know that ndiswrapper uses Windows drivers for WLAN cards as though they were native. Unfortunately, ndiswrapper has a bit to go before it becomes trully innovative software, IMHO.

Using ndiswrapper is easy.  Just place the *.INF (the driver for your card) in any folder.  Then run (without the curly braces):

 ```
$ ndiswrapper -i {driver}.inf
$ ndiswrapper -m
```

 To make sure that the driver is installed, run:

```
$ ndiswrapper -l
```

Lastly:

```
$ modprobe ndiswrapper
$ iwconfig
```

That should be it.  If anything would be left, restart the computer.

---

