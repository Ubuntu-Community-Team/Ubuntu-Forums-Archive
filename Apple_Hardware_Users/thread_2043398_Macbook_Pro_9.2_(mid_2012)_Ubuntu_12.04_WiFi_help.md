---
title: "Macbook Pro 9.2 (mid 2012) Ubuntu 12.04 WiFi help"
date: 2012-08-16
forum: Apple Hardware Users
---

### Post by jrdj on 2012-08-16
So i installed ubuntu 12.04 on my macbook pro 12.04 but the wifi does not work.
Tried a few things i have read on here but not luck.

Can any one try to help me out.
Im a bit of a ubuntu noob, sorry :)

---

### Post by adamski99 on 2012-08-16
I'm on the same system and using the 'b43' driver, its a bit of a faf to get going but there are posts and guides around google it. 

basically what i did was install b43-fwcutter, download the firmware from broadcom and and run the b43-fwcutter on it.

good luck :)

ads

---

### Post by jrdj on 2012-08-16
> **adamski99 said:**
> I'm on the same system and using the 'b43' driver, its a bit of a faf to get going but there are posts and guides around google it. 

basically what i did was install b43-fwcutter, download the firmware from broadcom and and run the b43-fwcutter on it.

good luck :)

ads

So you plunged an Ethernet cable in? and then installed b43-fwcutter, download the firmware from broadcom and and run the b43-fwcutter on it?

---

### Post by adamski99 on 2012-08-16
yes i did it with the ethernet plugged in.

before this i was getting some error like firmware missing when trying to load the b43 module:

```

sudo modprobe b43

```

cant remember the exact steps but i followed something like in this post:

[http://ubuntuforums.org/showpost.php?p=8788255&postcount=2](http://ubuntuforums.org/showpost.php?p=8788255&postcount=2)

to extract and install the firmware

hope it helps

cheers

ads

---

