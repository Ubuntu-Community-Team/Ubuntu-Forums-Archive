---
title: "How can I install QEMU"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2006-11-08
How can I install QEMU, if it's possible cause wine doesn't work with everything.
And how do you install qumo launcher

---

### Post by bodhi.zazen on 2006-11-08
QEMU is in the repositories.

[Enable repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

[How to QEMU](http://ubuntuforums.org/showthread.php?t=187413)

[alternate QEMU](http://ubuntuforums.org/showthread.php?t=39513)

---

### Post by Marsolin on 2006-11-08
Make sure to enable the universe section of the repos to get [QEMU]("http://linuxappfinder.com/package/qemu"). You might also be interested to check out [Qemu Launcher]("http://linuxappfinder.com/package/qemu-launcher") and [Qemuctl]("http://linuxappfinder.com/package/qemuctl"). They are both GUI interfaces for QEMU.

---

### Post by spyker3292 on 2006-11-08
> **Marsolin said:**
> Make sure to enable the universe section of the repos to get [QEMU]("http://linuxappfinder.com/package/qemu"). You might also be interested to check out [Qemu Launcher]("http://linuxappfinder.com/package/qemu-launcher") and [Qemuctl]("http://linuxappfinder.com/package/qemuctl"). They are both GUI interfaces for QEMU.

whats the repository for it? I know how to add more just dont know the http repo thing. And then it should show up as qemu in synaptic?

---

### Post by MasterOfDisaster on 2006-11-08
Are you planning to use QEMU as a replacement for wine?  If so, you may disappointed by the performance, as QEMU uses a emulation technique called binary emulation, and is rather slow.  If you have an AM2 Athlon CPU or Core/Core 2/9xx Pentium, you can run VMware or Xen to reap the benefits of hardware virtualization, which will run CPU-bound applications about 75% the speed of normal.

Anyways, there could be some faster alternatives if you are lucky enough to have a new CPU.

QEMU shows up as qemu in Synaptic, not sure about the interfaces.

---

### Post by spyker3292 on 2006-11-08
> **MasterOfDisaster said:**
> Are you planning to use QEMU as a replacement for wine?  If so, you may disappointed by the performance, as QEMU uses a emulation technique called binary emulation, and is rather slow.  If you have an AM2 Athlon CPU or Core/Core 2/9xx Pentium, you can run VMware or Xen to reap the benefits of hardware virtualization, which will run CPU-bound applications about 75% the speed of normal.

Anyways, there could be some faster alternatives if you are lucky enough to have a new CPU.

QEMU shows up as qemu in Synaptic, not sure about the interfaces.

Not a replacement just for things that don't work on WINE. I know it can be slow.

---

### Post by spyker3292 on 2006-11-08
Edit to main

---

### Post by spyker3292 on 2006-11-09
Bump

---

### Post by spyker3292 on 2006-11-09
Whatever I'm making a new thread

---

