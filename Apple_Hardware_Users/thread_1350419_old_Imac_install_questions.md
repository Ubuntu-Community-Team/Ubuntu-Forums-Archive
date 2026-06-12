---
title: "old Imac install questions"
date: 2009-12-09
forum: Apple Hardware Users
---

### Post by pelee98 on 2009-12-09
I have an old mac (one of those space-pod looking ones). It only has 64 meg of ram. Here's a link to the full specs:

[http://www.dealtime.com/xPF-Apple-AP...9-2-BLEU-Apple](http://www.dealtime.com/xPF-Apple-AP...9-2-BLEU-Apple)

I'm assuming I want xubuntu because of the low system capabilities?

Also, I need the alternate install CD, right?

Can someone post a link for the xubuntu alternate install CD? I can't seen to find it. 

And if you have a different version recommendation, let me know.

Thanks everyone.

---

### Post by linuxopjemac on 2009-12-09
[http://cdimage.ubuntu.com/xubuntu/ports/releases/karmic/release/xubuntu-9.10-alternate-powerpc.iso](http://cdimage.ubuntu.com/xubuntu/ports/releases/karmic/release/xubuntu-9.10-alternate-powerpc.iso)

---

### Post by linuxopjemac on 2009-12-09
when you have it running, pass us the info you get when you pass the following code:
```
sudo cat /proc/cpuinfo
```

We might be able to help you on X if we know which iMac you have, although I don't know if 64Mb is enough memory. Look here:
[http://wiki.xfce.org/minimum_requirements](http://wiki.xfce.org/minimum_requirements)

---

### Post by linuxopjemac on 2009-12-09
I found the answer:

> You need 192 MB RAM to run the Live CD or 128 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time.

To install Xubuntu, you need 2.0 GB of free space on your hard disk.

Once installed, Xubuntu can run with starting from 192 (or even just 128) MB RAM, but it is strongly recommended to have at least 256 MB RAM.

from [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

### Post by avtolle on 2009-12-09
The OP might want to consider a cli install from the alternate CD with a lightweight (IceWM, LXDE, etc.) window manager on that old hardware. I think such could run on 64mb RAM, albeit not quickly. [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) offers an alternative via the minimum install CD, which I've not tried.

---

