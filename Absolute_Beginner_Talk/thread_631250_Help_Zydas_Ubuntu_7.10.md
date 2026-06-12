---
title: "Help? Zydas? Ubuntu 7.10"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by benjmole on 2007-12-04
can someone give me a guide on how to install the drivers for the zydas zd1211 in ubuntu 7.10? it comes up in lsusb, but i just can't seem to figure it out?

it says on some websites that support is built in to the linux kernel?

any ideas?

thanks

---

### Post by benjmole on 2007-12-04
*bump*


please help.

---

### Post by shirilover on 2007-12-04
The ZyDAS zd1211 and zd1211b chipsets should be covered by the zd1211rw driver which is part of the kernel.
Try the following command:
```

lsmod

```
You should see zd1211rw, ieee80211, ieee80211_crypt, ieee80211_softmac loaded.
If not, use
```

sudo modprobe -v zd1211rw

```

---

### Post by benjmole on 2007-12-05
i tried that, didn't work. thanks for the reply.

any other ideas?

the adapter is branded as a pluscom adapter, but is based on the zydas chipset.

can ndiswrapper be used?

thanks

---

