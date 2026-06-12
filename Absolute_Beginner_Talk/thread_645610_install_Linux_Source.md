---
title: "install Linux Source"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by iroshan.net on 2007-12-20
I installed ubuntu from a DVD. When i going to install a driver it ask for kernel source. How to find source already  installed or how could i install it.

---

### Post by PmDematagoda on 2007-12-20
What Ubuntu version are you using?

If you do not know, then post the result of:-

```
uname -a
```

---

### Post by iroshan.net on 2007-12-20
Actually I want to install driver for TIUSB3140 Cable. That's for connect to internet using CDMA phone. But when compiling the source following message displayed... 
```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking os type... ok
checking kernel version... 2.6.22-14-386
checking kernel sources... found /lib/modules/2.6.22-14-386/build
checking usb-serial.h... not found

```

Is that header file makes the error.. if so how to solve that?

---

### Post by Bothered on 2007-12-20
Do you have build essentials installed?

```
sudo apt-get install build-essentials
```

---

### Post by Bothered on 2007-12-20
After a quick search (see [here]("http://www.linuxquestions.org/questions/linux-hardware-18/obscure-usb-serial-adapter-368278/page2.html?"))
it seems you need the full kernel source.

---

### Post by PmDematagoda on 2007-12-20
You can install the kernel source using:-

```
sudo apt-get install linux-source-2.6.22
```

---

