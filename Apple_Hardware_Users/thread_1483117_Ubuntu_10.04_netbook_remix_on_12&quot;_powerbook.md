---
title: "Ubuntu 10.04 netbook remix on 12&quot; powerbook"
date: 2010-05-14
forum: Apple Hardware Users
---

### Post by bigeasy_uk on 2010-05-14
I'd like to try Ubuntu netbook remix 10.04 on my 12" G4 Powerbook, but I can't seem to find it. Does it just not exist? Apple have a range of older 12" models that are no longer supported that Ubuntu would work great on so it would be a shame if it isn't possible.

---

### Post by linuxopjemac on 2010-05-14
I have never done it but I guess when you install Ubuntu, you can then opt for the ubuntu-netbook packages...

```
sudo apt-get install ubuntu-netbook
```

I would then just delete the ubuntu-desktop

```
sudo apt-get remove ubuntu-desktop
```

---

### Post by bigeasy_uk on 2010-05-14
Cheers linuxopjemac,

I'll give that a try and report back.

---

### Post by bigeasy_uk on 2010-05-14
OK, my install failed. Everything went through fine, rebooted after the install. I got an ascii version of the Ubuntu boot screen, then some corruption then a black screen, even the backlight went off, then nothing :-(. I'm gonna try a different install disc then hopefully post again from a working ubuntu install!

---

### Post by bigeasy_uk on 2010-05-14
It installed first time around with the new disc, so the first one was probably just a bad burn. Got the netbook packages installed and the desktop packages uninstalled fine too, so nice one for the advice linuxopjemac

---

