---
title: "up date did not work"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by greg m on 2006-08-26
hello 
i`m still geting fatal server error: no screen found after i ran the update. i tried everything or just about everything that was said here. that may be why it will not work.

(EE)unable to find a valid framebuffer device
(EE)nv (0)failed to open to open framebuffer device,consolt warnings and/or errors above for possible reasons

(ll)loading sub module "fbdevhw"
(llload module: "fbdevhw"
(llloading= /usr/lib/xorg/modules/linux/libfbdevhw.so
(ll) module fbdevhw: vendor="X.Org foundation" compiled for 7.0.o, module version=0.0.2 ABI class:X.org video driver, version 0.8
(WW) open /dev/fb1: no such file or dictory
fb2
fb3
fb4
fb5
fb6
fb7
(EE) Unable to find a valid framebuffer device
 see top

any ideas?

---

### Post by greg m on 2006-08-27
no one has any idea?

---

### Post by confused57 on 2006-08-27
Did you try downgrading the xserver version?
When you get the error message after booting up, press Ctrl+Alt+F1, login, then enter:

```
sudo dpkg -i /var/cache/apt/archives/xserver-xorg-core=1:1.0.2-0ubuntu10.deb
```

then

```
sudo reboot
```

Maybe you've already tried it...if you haven't, worth a shot.

---

