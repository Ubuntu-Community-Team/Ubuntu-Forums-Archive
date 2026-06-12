---
title: "vcdmount"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by benner on 2006-06-06
i am trying to mount a virtual drive.  i downloaded vcdmount from sourceforge.  unpacked it.  used the terminal.  got into the vcdmount-1.0 directory.  typed sudo make as instructed.  got sudo: make: command not found as an answer.  tried downloading different packages.  same thing each time.  am i doing something wrong?

---

### Post by Phasmagon on 2006-06-06
you should first install make either through synaptic or

sudo apt-get install make

but if you want to mount ISO images as part of your disk and not as a virtual CD there is fuseiso available.

sudo apt-get install fuseiso.

---

