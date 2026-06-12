---
title: "HELP! Broadcom SDA driver - nothing happens"
date: 2009-11-24
forum: Apple Hardware Users
---

### Post by slashdong on 2009-11-24
So I had to reinstall Ubuntu 9.10, and I was choosing trying to install the drivers. I managed to install the NVIDIA driver, but the Broadcom STA Wireless Driver will not install.

So I go to System>Hardware Drivers
I then choose Broadcom STA Wireless Driver, and select "Activate"
An authentication window pops up and i type in my password.
Then a small window that says "Downloading and installing" pops up... for about 2 seconds, then bursts into flames (closes).

I can't seem to install the driver manually from the Broadcom site (followed the ReadMe), either.
If it helps at all, I'm on a Macbook Pro (4,1) running Ubuntu 9.10 Karmic Koala in a triple boot config with OSX and Windows.

---

### Post by linds2009 on 2009-11-25
Sorry, did not encounter such a situation
I'll give those a try!

---

### Post by _mario_ on 2009-11-25
> **slashdong said:**
> 
So I go to System>Hardware Drivers
I then choose Broadcom STA Wireless Driver, and select "Activate"
An authentication window pops up and i type in my password.
Then a small window that says "Downloading and installing" pops up... for about 2 seconds, then bursts into flames (closes).


I don't know what System>Hardware Drivers actually does behind the scenes, but running:
```

sudo apt-get install bcmwl-kernel-source bcmwl-modaliases

```
and rebooting should be sufficient.

> **slashdong said:**
> 
I can't seem to install the driver manually from the Broadcom site (followed the ReadMe), either.
If it helps at all, I'm on a Macbook Pro (4,1) running Ubuntu 9.10 Karmic Koala in a triple boot config with OSX and Windows.

Don't try that unless you're really comfortable in compiling drivers yourself.

ciao,
Mario

---

