---
title: "ndiswrapper help"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by greyash99 on 2006-07-16
ive installed ndiswrapper and I have the driver but I don't know how to install it.  I have a  Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
.

---

### Post by Jagot on 2006-07-16
I have a Broadcom 4318 and this is how I do it:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

The first section actually installs the driver.  The second section blacklists the built-in Broadcomdrivers in Ubuntu (which don't work for me).

---

### Post by orb9220 on 2006-07-16
Hope it works.

But you might want to post in the network or wireless forums they have all kinds of NDIS wrapper stuff.

May get more help than in Beginner talk.

Just a thought.

---

