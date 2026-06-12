---
title: "Q [kju] help"
date: 2006-11-19
forum: Apple PPC Users
---

### Post by sbentzen on 2006-11-19
i need help making a guest pc on apple hardware for ubuntu, can anyone help? thankyou in advance

---

### Post by EuroCity on 2006-11-20
It will be really sloooooooooow with Q (or Qemu): Virtual PC, in comparison, flies!

Expect an entire day or so to install Ubuntu on Q...

Maybe a little faster on an Intel Mac, anyway: but, sadly, the kqemu accelerator module hasn't yet been ported to Mac OS X (Intel).

Anyway, you should create a new PC from within Q, unchecking the "Set clock to host time" checkbox in the first panel (Ubuntu defaults to UTC if it doesn't detect any Windows partitions), and then setting up an x86 PC with at least 256 MB RAM in the second pane, with (optionally) ENSONIQ sound card and NE2000 network adapter; then, create a disk image of at least 10 GB (10240 MB) or so, select the Ubuntu (x86) Desktop CD image and boot from CD-ROM (after the install, after having shut down the VM, you should set this back to boot from the hard drive): then, press the "Create PC" button, of course. 

All this should be OK to start the virtual machine (slowly) and install Ubuntu from the live CD (which is faster than the alternate one), as on a real PC...

---

