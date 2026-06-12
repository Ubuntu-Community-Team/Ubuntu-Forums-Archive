---
title: "VirtualBox"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by jamieh on 2007-08-01
Will running VirtualBox allow me to run ***_[COLOR="Red"]ANY[/COLOR]_*** Windows program? And will the guest OS detect all my hardware as if it were on a separate partition?

---

### Post by felicity on 2007-08-01
It will run most programs, unless you want to play directx games or something... It doesn't detect your hardware in the same way as having a dual boot. The virtual machine is "virtual hardware" instead.

---

### Post by bodhi.zazen on 2007-08-01
No. Some programs do not run.

No. Virtualbox and VMware EMULATE HARDWARE. They do not run your native hardware, that is why you may have some software limitations.

For example you can not run compiz in Virtualbox no matter your hardware or host os. This is because the virtual video card does not support such effects even if you have a compatible video card.

Booting a hard drive is an advanced topic and IMO in alpha development. There may be problems, including data loss ...

---

