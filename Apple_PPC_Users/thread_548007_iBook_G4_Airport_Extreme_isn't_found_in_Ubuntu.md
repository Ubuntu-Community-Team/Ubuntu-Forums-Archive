---
title: "iBook G4 Airport Extreme isn't found in Ubuntu"
date: 2007-09-10
forum: Apple PPC Users
---

### Post by BSBarrows on 2007-09-10
I am running Ubuntu 7.04 on PPC ibook, from the CD, I don't know if this is the problem, but I haven't been able to get the wireless to work. Eventually I will partition the HD and do a Tiger/Ubuntu thing, but I want to get to know it better. To boot, I am new with Ubuntu and would like a step by step here for what to use and how to use it. I am good with computers, just this Ubuntu is killing me right now, but got to love the interface, login, everything else about it! Thanks to anyone that can help.

---

### Post by dynamicv on 2007-09-11
Have you tried the steps outlined in [this]("http://ubuntuforums.org/showthread.php?t=468974") thread?  I found that after installing the AE firmware I had to remove the Network Manager software to get a reliable wireless conneciton.  Mine is working over WPA-PSK using wpasupplicant.

Once you've put the firmware on there use the "iwlist scan" command to test whether the interface is working properly.  You can then continue getting the WEP/WPA working.

One thing I've noticed though is that the wireless range isn't as good as in OSX on the same hardware.  You may want to set the configuration up whilst sat quite close to your access point until you have it all working, to make sure you're not wasting time.

---

### Post by stmiller on 2007-09-11
Just do this:
```

sudo apt-get install bcm43xx-fwcutter

```

That's it.

---

