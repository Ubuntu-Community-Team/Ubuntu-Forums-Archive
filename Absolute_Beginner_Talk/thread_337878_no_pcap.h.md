---
title: "no pcap.h"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by SimonNewbie on 2007-01-13
Hello - I am trying to get wepattack installed and have installed the 0.9.4-1 libpcap pacakge and then trying to make the wepattack but it's moaning saying the pcap.h file is not there. Is there another package I have to install to get this file? I think I am getting there and hoping this this file is part of a package or do I have to look into installing this library in another way?

Thanks,
Simon

---

### Post by Hossie on 2007-01-13
If you want to compile something and need the C-headers of a library, you always need the -dev package.

```
sudo apt-get install libpcap0.8-dev
```

---

### Post by SimonNewbie on 2007-01-14
thanks for that - got me a step closer, roll on the next problem

---

