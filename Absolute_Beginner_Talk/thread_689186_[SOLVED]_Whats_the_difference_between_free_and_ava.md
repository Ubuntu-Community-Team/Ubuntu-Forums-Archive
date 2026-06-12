---
title: "[SOLVED] Whats the difference between free and available space on a HDD?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2008-02-06
Hi,

i want to free up some space on a spare HDD.(that has 45.1free and 21.8 available)

a suggestion was:

firebox@firebox-desktop:~$ tune2fs -m 0 /dev/sda1
tune2fs 1.40.2 (12-Jul-2007)
tune2fs: Permission denied while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
firebox@firebox-desktop:~$ 

any ideas?

---

### Post by hyper_ch on 2008-02-06
run it as sudo

---

### Post by hopelessone on 2008-02-06
sudo tune2fs -m 0 /dev/sda1
 sudo sudo sudo...got it...

---

### Post by mikeyphi on 2008-02-06
> **hopelessone said:**
> Hi,

i want to free up some space on a spare HDD.(that has 45.1free and 21.8 available)

a suggestion was:

firebox@firebox-desktop:~$ tune2fs -m 0 /dev/sda1
tune2fs 1.40.2 (12-Jul-2007)
tune2fs: Permission denied while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
firebox@firebox-desktop:~$ 

any ideas?

Possibly free=not formatted; available=formatted and unused?

Install gparted from Synaptic - that will show you drives in full. (although some types of format are not supported- for a fuller experience you could use 'testdisk' also from Synaptic!)

---

