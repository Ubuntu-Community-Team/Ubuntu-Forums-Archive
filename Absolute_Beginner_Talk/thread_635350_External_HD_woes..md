---
title: "External HD woes."
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by slackmaster on 2007-12-08
Hello Ubuntu forum,

Ubuntu is the best but it can get tricky.  I recently plugged in my 150GB MyBook External HD to see if I can access it in Ubuntu.  Normally I use it with my windows machine.  Well Ubuntu cannot mount the drive.
Next issue,  I wanted to manage my Rio Ce2100 Mp3 player and my Nano Ipod with Amarok.  At first the CE2100 was easy to access.  I moved all my music file onto my desktop.  But after rebooting, the RIO is just dead...lifeless. I mainly wanted to transfer some new files from one of the Ubuntu media players onto my Rio.  But now it is dead.  Any idea why that might happen?

So I tried my Ipod with Amarok.  But Amarok will not recognize the Ipod.  I tried mounting it manually but it still does not recognize it.  I tried making it my defaul player but Hald is not running.  So I went into services but I do not see how to start Hald.

Thanks ahead of time for any tips.

external HD won't mount, Rio Ce 2100 dies, and Ipod will not mount because Hald is not running but I can't find how to run Hald.  Volume management is not supported.

Slack.

---

### Post by lamalex on 2007-12-08
To start hal, try this
```
sudo /etc/init.d/hal stop
sudo /etc/init.d/hal start
```

If it starts, that may also fix your external drive problem.

---

