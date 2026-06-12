---
title: "Help with wireless connection on a MacBook."
date: 2009-12-15
forum: Apple Hardware Users
---

### Post by Ubu4moi on 2009-12-15
I installed Ubuntu 9.04 on a MacBook and I can't seem to be able to use the wireless on the laptop. The icon shows it is not connected and I can't find anything to turn it on. Help anyone... also how can I install the iCamera?

---

### Post by linuxopjemac on 2009-12-15
Hook it up to an internet cable and run:
```
sudo apt-get update
sudo apt-get upgrade

```
then go to Administration -> Hardware drivers. Try to find a driver.

If your network card already works (check in command line:)
```
iwconfig
```

you should see a wireless entry.

If so, and networkmanager still does not work, you can try to install wicd, which is sometimes working better than networkmanager for some people
```
sudo apt-get install wicd
```
networkmanager will automatically be suppressed.

---

