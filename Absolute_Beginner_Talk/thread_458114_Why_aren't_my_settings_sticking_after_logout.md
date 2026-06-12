---
title: "Why aren't my settings sticking after logout?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by darkmage77 on 2007-05-29
So far, I'm having a blast with Ubuntu. Almost everything I did in Windows I'm finding I can do with almost no hassle. But I am having a bit of a problem with settings.

There may be more issues that I haven't uncovered yet, but the 2 I'm annoyed with the most are:

1) If I have to restart Ubuntu, I'll have to restart a second time because my eth0 won't initialize.

2) I have an NTFS partition that I have to remount _every_ time Ubuntu is started.

Is there any way to make these settings persist? It's not a dealbreaker as far as I'm concerned, but it is a bit annoying.

Any ideas?

---

### Post by Kobalt on 2007-05-29
1. Can you please post the output of ```
cat /etc/network/interfaces
``` (make sur to remove any personal info)
2. Check this out : [https://help.ubuntu.com/community/MountNtfsOnBoot](https://help.ubuntu.com/community/MountNtfsOnBoot)

---

### Post by lazyart on 2007-05-29
Instead of rebooting for eth0, try```
sudo ifdown eth0
sudo ifup eth0
```I do this when I have issues with my wireless (though it's ath0, same idea).  To disconnect and reconnect all adapters, use -a instead of eth0.

For mounting the partition you can edit /etc/fstab.  I don't have that answer handy but someone will real soon I'm sure, or search for it if you can't wait. :)

---

### Post by darkmage77 on 2007-05-29
> **Kobalt said:**
> 1. Can you please post the output of ```
cat /etc/network/interfaces
``` (make sur to remove any personal info)

Sure, it was:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

