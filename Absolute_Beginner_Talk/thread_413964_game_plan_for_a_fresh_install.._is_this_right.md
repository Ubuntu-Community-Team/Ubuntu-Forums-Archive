---
title: "game plan for a fresh install.. is this right?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by s9am_me on 2007-04-19
I currently dual boot XP and Edgy on my laptop with 20GB each partition.  Planning to do a clean install as I want to start from scratch but still want my XP partition in tact.  My edgy install works fine but I just feel more comfortable with clean installs.  I've read through a bunch of posts here and concluded with the following steps:

- restore my old MBR first by booting my XP CD, recovery mode and run "fixmbr"
- restart and hopefully it will boot XP automatically
- delete the ubuntu partition in XP using a disk partitioner
- restart and boot with the Feisty live CD and install Feisty on the unpartitioned space

am I missing something else? Are those the correct steps to take?

---

### Post by Seisen on 2007-04-19
If your planning on using grub then you don't have to worry about fixing the Windows MBR.

---

### Post by lamalex on 2007-04-19
why can't you just straight up reinstall? why bother with the other stuff, just boot to feisty, put it only on your ubuntu partitions, and then you're good to go. that's what I've done in the past with no problem

---

### Post by s9am_me on 2007-04-19
if I delete my ubuntu partition, GRUB will give me an error looking for Ubuntu won't it?  I heard people posting when they deleted Ubuntu, messed up GRUB and could boot to any OS.  So should I just delete the Ubuntu partition under windows or can I do it via the live cd install?

---

### Post by s9am_me on 2007-04-19
> **Iamalex said:**
> why can't you just straight up reinstall? why bother with the other stuff, just boot to feisty, put it only on your ubuntu partitions, and then you're good to go. that's what I've done in the past with no problem

ok that's what I thought.  thanks

---

