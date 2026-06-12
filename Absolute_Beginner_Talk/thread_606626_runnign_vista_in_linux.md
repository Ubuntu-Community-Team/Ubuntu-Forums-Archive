---
title: "runnign vista in linux"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by aerris on 2007-11-08
so is it possible to boot linux on a dual boot machine and then boot the other OS partition (in this case Vista) in some kind of window in ubuntu?

To run both os at the same time from the same HDD?

thanks

---

### Post by TadH on 2007-11-08
im pretty sure it is, i saw it around here somewhere did u searvch the forums?

---

### Post by AlexenderReez on 2007-11-08
hm...try to use 


1. [virtualbox]("http://www.virtualbox.org/")

or


2. [qemu]("http://fabrice.bellard.free.fr/qemu/")

---

### Post by anaconda on 2007-11-08
It is possible to run windows from a partition in vmware, but it isnt that easy. And you might run into activation problems.. because vista would detect that almost all hardware has changed, because vmware emulates virtual hardware..

It would be much easier to install windows to a virtual disk, which would be on your ubuntu partition, and which could be run only through vmware (or virtualbox, or qemu)

---

### Post by shafin on 2007-11-08
TO run an installation off a real hard drive,you'll need VMware,But virtualbox is great with its seamless integration.

---

### Post by CalvinK on 2007-11-18
> **AlexenderReez said:**
> hm...try to use 


1. [virtualbox]("http://www.virtualbox.org/")

or


2. [qemu]("http://fabrice.bellard.free.fr/qemu/")

I failed running the preinstalled Vista on my Toshiba A200 with qemu. However, it is the first time I try. I'm still trying ... I will post something if I succeed.

---

### Post by shoaibi on 2007-11-18
i found VMware Server more fascinating, i can connect to any virtual machine in my ALN and do whatever i want,
virtualbox is also cool...

---

